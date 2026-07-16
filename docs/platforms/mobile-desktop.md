# Mobile and desktop application routes

Choose the platform route based on product requirements, team skills, native integration, distribution, and long-term maintenance—not only the ability to render the first screen.

## Mobile with React Native and Expo

**Recommended** when React skills should transfer to iOS and Android and the required native capabilities are available through Expo or maintained React Native libraries.

- [React Native environment setup](https://reactnative.dev/docs/environment-setup)
- [Expo documentation](https://docs.expo.dev/)
- [Create an Expo project](https://docs.expo.dev/get-started/create-a-project/)
- [Expo Application Services](https://docs.expo.dev/eas/)
- [React Navigation](https://reactnavigation.org/docs/getting-started/)

Use Expo's managed capabilities unless a specific native dependency requires a different workflow. Validate notifications, deep links, background behavior, permissions, store signing, and offline behavior early.

## Mobile and desktop with .NET MAUI

**Recommended alternative** when C# reuse, Microsoft ecosystem integration, and one shared project across Android, iOS, macOS, and Windows provide the best organizational fit.

- [.NET MAUI documentation](https://learn.microsoft.com/en-us/dotnet/maui/?view=net-maui-10.0)
- [.NET MAUI supported platforms](https://learn.microsoft.com/en-us/dotnet/maui/supported-platforms?view=net-maui-10.0)
- [.NET MAUI architecture guidance](https://learn.microsoft.com/en-us/dotnet/architecture/maui/)
- [.NET MAUI Community Toolkit](https://learn.microsoft.com/en-us/dotnet/communitytoolkit/maui/)

Confirm platform-specific SDK and build-host requirements before committing to the delivery schedule, particularly for iOS and macOS.

## Desktop with Avalonia

**Recommended** for cross-platform desktop applications where C#, XAML-style UI, Linux support, and a desktop-first architecture are important.

- [Avalonia documentation](https://docs.avaloniaui.net/)
- [Avalonia getting started](https://docs.avaloniaui.net/docs/get-started/)
- [Avalonia controls](https://docs.avaloniaui.net/controls)

Use Avalonia when the application is fundamentally a desktop product rather than a mobile application extended to desktop.

## Desktop with Tauri

**Recommended** for a small native shell around a React, Angular, or other web frontend when native capabilities can be exposed through a narrow Rust command surface.

- [Tauri v2 getting started](https://v2.tauri.app/start/)
- [Tauri architecture](https://v2.tauri.app/concept/architecture/)
- [Tauri security](https://v2.tauri.app/security/)
- [Tauri distribution](https://v2.tauri.app/distribute/)

Treat every native command as a privileged boundary. Validate arguments, constrain file-system and process access, and grant the frontend only the capabilities it needs.

## Desktop with Electron

**Alternative** when mature Node.js desktop integrations, Chromium consistency, or an existing Electron ecosystem dependency outweigh package size and memory cost.

- [Build your first Electron application](https://www.electronjs.org/docs/latest/tutorial/tutorial-first-app)
- [Electron security](https://www.electronjs.org/docs/latest/tutorial/security)
- [Electron Forge](https://www.electronforge.io/)

Keep context isolation enabled, disable unnecessary Node.js exposure in renderer processes, and use a narrow preload API.

## Progressive Web App

**Alternative** when installation, offline behavior, notifications, and device integration requirements can be satisfied by modern web capabilities without store-specific native distribution.

- [Progressive web apps on MDN](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps)
- [Service Worker API](https://developer.mozilla.org/en-US/docs/Web/API/Service_Worker_API)
- [Web app manifests](https://developer.mozilla.org/en-US/docs/Web/Progressive_web_apps/Manifest)

Validate platform support for every critical capability; PWA support is not uniform across browsers and operating systems.

## Selection guide

| Requirement | Preferred route |
| --- | --- |
| Share React skills with mobile | React Native + Expo |
| Share C# across mobile and desktop | .NET MAUI |
| Desktop-first C# application, including Linux | Avalonia |
| Lightweight web UI with native Rust shell | Tauri |
| Node.js desktop ecosystem is decisive | Electron |
| No native-only capability and web distribution is enough | PWA |

## Capabilities to validate early

- Authentication redirects and secure token storage.
- File-system, camera, microphone, Bluetooth, USB, NFC, and location access.
- Push notifications and background execution.
- Offline synchronization and conflict resolution.
- Automatic updates and rollback.
- Crash reporting and telemetry.
- Code signing, notarization, application-store requirements, and enterprise deployment.
- Accessibility with keyboard, touch, screen readers, scaling, and high contrast.
