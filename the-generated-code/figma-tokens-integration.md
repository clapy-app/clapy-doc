---
description: >-
  Clapy partners with the team of Figma Tokens, a plugin that helps to design on
  Figma using design tokens.
---

# Figma Tokens integration

{% hint style="info" %}
Any question about the design decisions? Anything not matching your project practices? [Please let us know](https://clapy.co/contact)! we may add an option for the flexibility you need.
{% endhint %}

Clapy seamlessly extracts the design tokens managed by [Figma Tokens](https://www.figmatokens.com/) and generates code leveraging them.

For example, let’s say you have defined your colors, fonts, spacings… using Figma Tokens. When generating code with Clapy, tokens will be extracted seamlessly and included in the output project as CSS variables, in `src/variables.css`.

```css
:root {
  --spacing-scale: 2px;
  --spacing-xs: 4px;
  --spacing-sm: 8px;
  --spacing-md: 16px;
  --spacing-lg: 32px;
  --spacing-xl: 64px;
  --sizing-scale: 1.5px;
  /* ... */
}
```

Components will use those variables following the Figma Tokens configuration, e.g.:

```css
.card {
  padding: var(--spacing-xs);
}
```

When a style doesn’t have a variable defined, it falls back to the Figma values, e.g.:

```css
.card {
  padding: var(--spacing-xs);
  width: 300px;
}
```

Clapy embeds a fork of [Style Dictionary](https://amzn.github.io/style-dictionary) to generate the variables, which is useful to generate a fully working project. But you’re free to setup your own pipeline generating variables from Figma Tokens, and include them in the target project. The components will refer to those variables following the Style Dictionary and Figma Tokens standards.
