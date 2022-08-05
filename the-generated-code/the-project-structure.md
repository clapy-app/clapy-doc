---
description: >-
  Many best practices have been included by default to ensure you get a good
  starting point for most cases.
---

# The project structure

{% hint style="info" %}
Any question about the design decisions? Anything not matching your project practices? [Please let us know](https://clapy.co/contact)! we may add an option for the flexibility you need.
{% endhint %}

### Frameworks

Two frameworks are available: **React** and **Augular** (alpha).

Angular does not yet has all the features available in React (e.g. customizable components).

### Base template

By default, the project is uploaded on [Codesandbox](https://codesandbox.io/) for a super fast preview without needing to install anything.

All projects use [TypeScript](https://www.typescriptlang.org/) to type your variables.

#### React

The project uses create-react-app, which is better supported on Codesandbox.

If you decide to download as a zip instead, the project uses [ViteJS](https://vitejs.dev/) for crazy fast development builds.

#### Angular

The project uses the Angular CLI template.

### Files structure

Entry points are specific to the base template:

* Codesandbox:
  * `index.html` is in `public`,
  * The TypeScript entry point is `src/index.tsx`.
* ViteJS:
  * `index.html` is in the root directory,
  * The TypeScript entry point is `src/main.tsx`.

The generated code is component-oriented. The selected Figma element is treated as a component (even if it’s not a component in Figma). Its code is located in:

```html
src/components/ComponentName/ComponentName.tsx
```

With _ComponentName_ being defined as described in the [Naming conventions section](the-project-structure.md#naming-conventions). Sub-components are located in a sub-folder.

Example: Let’s assume we code a `Card` component that contains an instance of `Actions`, which contains two `Button`s. The generated code will be structured this way:

* src/components/Card (directories)
  * Actions (directory)
    * Actions.tsx (file)
  * Button (directory)
    * Button.tsx (file)
  * Icon (directory)
    * Icon.tsx (file)
  * Card.tsx (file)

{% hint style="info" %}
Currently, Clapy generates a single page and its sub-components. Soon, we will add the ability to include multiple frames as pages with the components they depend on. The file structure will be improved to better match common practices, with settings to choose the pages and components directory.

Any opinion about how files should be structured? [Please let us know](https://clapy.co/contact)
{% endhint %}

### Naming conventions

All **components** are named using the name of the corresponding Figma element, following the upper-case CamelCase convention.

Similarly, on each node, **classNames**, other **properties** and **variables** are deduced from the corresponding Figma element, using the lower-case camelCase convension.

For SVGs, an “Icon” suffix is added to the SVG name.

### App.tsx

It contains a reference to the main component. If the Figma selection is an instance, App.tsx will also provide the required overrides to the instance to match the design. Please refer to the [instances article](instances.md) for more details about the overrides.

### Styles

Styles are provided as CSS modules and located next to the component. Example:

* src/components/Card (directories)
  * Card.module.css (file)
  * Card.tsx (file)

### SVG

Shapes on Figma (rectangles, stars, vectors…) are converted to SVG files

#### React

SVGs are bundled into a React component. They are located in the same directory as the React component using them.

Example: let’s say a Button contains an ArrowIcon. We get the structure:

* src/components/Button (directories)
  * ArrowIcon.tsx (file)
  * Button.tsx (file)

#### In Angular, SVGs

SVGs are kept in `.svg` files, located in `src/assets`. They are displayed using the `<img />` tag.

### Images

Images are extracted from Figma and added to the source code in the `public` directory.

When the CSS points to an image (e.g. background-image url), it uses the relative link that will be correct at runtime, in the browser. Not the relative path in the source code between the CSS file and the asset file. Bundlers should leave those URLs as they are.

Any issue with it? Please let us know!

#### Global resets

`src/resets.css` contains global CSS rules to have defaults closer to the Figma behavior.

### Other tools in the project

ESLint and Prettier are included for opinionated code linting and formatting.
