# Recipe: React + Vite + Microsoft Entra SPA

Use this recipe to start a React + TypeScript single-page application authenticated with Microsoft Entra through MSAL.

This is a practical companion to the official [Microsoft Entra React SPA tutorial](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-single-page-app-react-prepare-app). The official tutorial explains MSAL concepts but may use a different project generator; this recipe uses Vite.

## 1. Create the application

```bash
npm create vite@latest my-app -- --template react-ts
cd my-app
npm install
npm install @azure/msal-browser @azure/msal-react
npm run dev
```

Record the local origin displayed by Vite, normally `http://localhost:5173`.

## 2. Register the SPA

In Microsoft Entra:

1. Create or select an app registration.
2. Record the application or client ID.
3. Record the tenant ID or external-tenant authority.
4. Add a **Single-page application** redirect URI matching the local Vite origin.
5. Add the production redirect URI before deployment.
6. Add delegated API permissions and consent only when the application needs them.

References:

- [Register an application](https://learn.microsoft.com/en-us/entra/identity-platform/quickstart-register-app)
- [Redirect URI restrictions](https://learn.microsoft.com/en-us/entra/identity-platform/reply-url)
- [Microsoft Entra External ID](https://learn.microsoft.com/en-us/entra/external-id/)

## 3. Add public environment configuration

Create `.env.local`:

```dotenv
VITE_ENTRA_CLIENT_ID=00000000-0000-0000-0000-000000000000
VITE_ENTRA_AUTHORITY=https://login.microsoftonline.com/organizations
VITE_ENTRA_REDIRECT_URI=http://localhost:5173
```

Add `.env.local` to `.gitignore` if the repository does not already ignore local environment files.

These values configure a public client and are not client secrets. Nevertheless, keep environment-specific configuration out of committed source. Never put a client secret, API key, or confidential credential in a Vite variable; every `VITE_` value can be exposed to the browser bundle.

For an external tenant, use the authority format required by the tenant and configure `knownAuthorities` when applicable. Follow the official External ID steps rather than reusing a workforce authority blindly.

## 4. Create the MSAL configuration

Create `src/authConfig.ts`:

```ts
import { type Configuration, LogLevel } from '@azure/msal-browser';

const clientId = import.meta.env.VITE_ENTRA_CLIENT_ID;
const authority = import.meta.env.VITE_ENTRA_AUTHORITY;
const redirectUri = import.meta.env.VITE_ENTRA_REDIRECT_URI;

if (!clientId || !authority || !redirectUri) {
  throw new Error('Missing Microsoft Entra configuration.');
}

export const msalConfig: Configuration = {
  auth: {
    clientId,
    authority,
    redirectUri,
    postLogoutRedirectUri: redirectUri,
    navigateToLoginRequestUrl: true,
  },
  cache: {
    cacheLocation: 'sessionStorage',
  },
  system: {
    loggerOptions: {
      piiLoggingEnabled: false,
      loggerCallback: (level, message, containsPii) => {
        if (containsPii) return;

        switch (level) {
          case LogLevel.Error:
            console.error(message);
            break;
          case LogLevel.Warning:
            console.warn(message);
            break;
          case LogLevel.Info:
            console.info(message);
            break;
          case LogLevel.Verbose:
            console.debug(message);
            break;
        }
      },
    },
  },
};

export const loginRequest = {
  scopes: ['openid', 'profile', 'email'],
};
```

Add API scopes separately when the SPA must call a protected API. Do not request permissions the application does not use.

## 5. Initialize MSAL before rendering React

Replace `src/main.tsx` with:

```tsx
import { StrictMode } from 'react';
import { createRoot } from 'react-dom/client';
import {
  EventType,
  PublicClientApplication,
  type AuthenticationResult,
} from '@azure/msal-browser';
import { MsalProvider } from '@azure/msal-react';
import App from './App.tsx';
import { msalConfig } from './authConfig.ts';
import './index.css';

const msalInstance = new PublicClientApplication(msalConfig);

await msalInstance.initialize();
await msalInstance.handleRedirectPromise();

const existingAccount = msalInstance.getAllAccounts()[0];
if (!msalInstance.getActiveAccount() && existingAccount) {
  msalInstance.setActiveAccount(existingAccount);
}

msalInstance.addEventCallback((event) => {
  if (event.eventType === EventType.LOGIN_SUCCESS && event.payload) {
    const result = event.payload as AuthenticationResult;
    msalInstance.setActiveAccount(result.account);
  }
});

createRoot(document.getElementById('root')!).render(
  <StrictMode>
    <MsalProvider instance={msalInstance}>
      <App />
    </MsalProvider>
  </StrictMode>,
);
```

Initializing the client explicitly avoids using MSAL before it is ready and makes redirect handling part of application startup.

## 6. Add sign-in and sign-out

Use a small component such as:

```tsx
import {
  AuthenticatedTemplate,
  UnauthenticatedTemplate,
  useMsal,
} from '@azure/msal-react';
import { loginRequest } from './authConfig';

export function AccountControls() {
  const { instance } = useMsal();
  const account = instance.getActiveAccount();

  return (
    <>
      <AuthenticatedTemplate>
        <span>{account?.name ?? account?.username}</span>
        <button type="button" onClick={() => void instance.logoutRedirect()}>
          Sign out
        </button>
      </AuthenticatedTemplate>

      <UnauthenticatedTemplate>
        <button
          type="button"
          onClick={() => void instance.loginRedirect(loginRequest)}
        >
          Sign in
        </button>
      </UnauthenticatedTemplate>
    </>
  );
}
```

Replace raw buttons with the application's chosen component system, such as Fluent UI React v9.

## 7. Call a protected API

1. Expose a delegated scope from the API app registration.
2. Grant that scope to the SPA registration.
3. Add the scope to a separate token request.
4. Acquire a token silently first.
5. Fall back to an interactive request only when MSAL reports that interaction is required.
6. Send the access token to the API through the `Authorization: Bearer` header.
7. Validate issuer, audience, lifetime, and authorization policy in the API.

References:

- [Acquire and cache tokens with MSAL.js](https://learn.microsoft.com/en-us/entra/identity-platform/msal-acquire-cache-tokens)
- [Protected web API overview](https://learn.microsoft.com/en-us/entra/identity-platform/scenario-protected-web-api-overview)
- [Microsoft.Identity.Web](https://learn.microsoft.com/en-us/entra/msal/dotnet/microsoft-identity-web/)

Never treat the ID token as the API access token.

## 8. Add route behavior

Route guards improve user experience, but the API remains the authorization boundary. A user who cannot see a route in React may still construct an HTTP request manually.

Preserve the intended route before redirecting to sign-in when that improves the return experience.

## 9. Validate

- Sign in and sign out.
- Refresh while authenticated.
- Open the application in a second tab.
- Test expired token recovery.
- Test a user without the required role or scope.
- Test workforce or external-tenant behavior as applicable.
- Confirm production redirect and logout URIs.
- Confirm that no secrets appear in source maps, browser storage, network calls, or the compiled bundle.
- Run linting, unit tests, and Playwright for the critical sign-in journey.

## 10. Production decisions

Document:

- Workforce versus external identity.
- Tenant restrictions and account-selection rules.
- Session and token-cache behavior.
- Roles, groups, scopes, and consent.
- Custom authentication domain when used.
- Backend authorization policies.
- Error and support path for failed sign-in.
- Telemetry that excludes tokens and unnecessary personal information.

## Official references

- [Microsoft Entra React SPA tutorial](https://learn.microsoft.com/en-us/entra/identity-platform/tutorial-single-page-app-react-prepare-app)
- [MSAL React](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/lib/msal-react)
- [MSAL Browser](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/lib/msal-browser)
- [Vite environment variables](https://vite.dev/guide/env-and-mode)
- [Fluent UI React v9](https://react.fluentui.dev/)
