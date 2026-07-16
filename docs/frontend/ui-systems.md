# UI systems and visual foundations

Choose a coherent interface system before selecting individual controls. A component library is not a substitute for information architecture, interaction design, responsive behavior, or accessibility.

## Preferred routes

### Fluent UI 2

**Recommended** for product interfaces that should feel native to the Microsoft ecosystem or follow Fluent design principles.

- [Fluent 2 design system](https://fluent2.microsoft.design/)
- [Fluent UI React v9](https://storybooks.fluentui.dev/react/)
- [Fluent UI Web Components](https://learn.microsoft.com/en-us/fluent-ui/web-components/)
- [Fluent UI GitHub repository](https://github.com/microsoft/fluentui)

Use design tokens and theme providers rather than hard-coded colors. Define light, dark, and high-contrast behavior from the start.

### Bootstrap

**Recommended alternative** for landing pages, internal systems, prototypes, and administration interfaces where delivery speed and familiar responsive primitives are the priority.

- [Bootstrap 5.3](https://getbootstrap.com/docs/5.3/getting-started/introduction/)
- [React Bootstrap](https://react-bootstrap.github.io/)
- [ng-bootstrap](https://ng-bootstrap.github.io/)

Prefer Bootstrap utilities and tokens over deeply overriding component internals. If extensive overrides are required, a design-system-first route may be more maintainable.

## CSS foundations

- [MDN CSS guides](https://developer.mozilla.org/en-US/docs/Learn_web_development/Core/Styling_basics)
- [CSS custom properties](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Cascading_variables/Using_custom_properties)
- [CSS Grid](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Grid_layout)
- [Flexbox](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Flexible_box_layout)
- [Container queries](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Containment/Container_queries)

Use native CSS capabilities before adding a utility framework solely to solve layout or theming.

## Icons and typography

- [Fluent System Icons](https://github.com/microsoft/fluentui-system-icons)
- [Typography in Windows and Segoe UI Variable](https://learn.microsoft.com/en-us/windows/apps/design/signature-experiences/typography)

Do not use icons without accessible names when they trigger actions. Do not use an icon as the only explanation for an unfamiliar operation.

## Accessibility

- [Web Content Accessibility Guidelines](https://www.w3.org/WAI/standards-guidelines/wcag/)
- [WAI-ARIA Authoring Practices](https://www.w3.org/WAI/ARIA/apg/)
- [MDN accessibility guide](https://developer.mozilla.org/en-US/docs/Web/Accessibility)
- [Accessibility Insights](https://accessibilityinsights.io/)
- [axe-core](https://github.com/dequelabs/axe-core)

Minimum expectations:

- Semantic HTML before ARIA.
- Complete keyboard navigation.
- Visible focus states.
- Sufficient contrast.
- Labels, errors, and instructions associated with form controls.
- Reduced-motion support when animation is not essential.
- Automated checks supplemented by keyboard and screen-reader review.

## Responsive design

Design around content constraints rather than a list of device models. Validate at narrow, medium, and wide widths, with zoom and enlarged text, and with touch as well as pointer input.

## Selection rule

Use one primary system per product. A secondary library may be added only for a capability the primary system cannot reasonably provide, and the visual and accessibility implications should be documented.
