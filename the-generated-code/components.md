---
description: >-
  React components include common best practices for good performances,
  maintainability and ease of use. Here are some of the design decisions for the
  generated code.
---

# Components

{% hint style="info" %}
Any question about the design decisions? Anything not matching your project practices? [Please let us know](https://clapy.co/contact)! we may add an option for the flexibility you need.
{% endhint %}

### Naming conventions

[They are described here](the-project-structure.md#naming-conventions).

### Functional components

Clapy components are written using functions. Most modern React code is written using functions and hooks. It can remain simple and most libraries will provide their features as [hooks](https://reactjs.org/docs/hooks-overview.html#but-what-is-a-hook) rather [HOC](https://reactjs.org/docs/higher-order-components.html) or other class-specific implementations.

### Memoization

We consider components should be memoized by default, which should be beneficial in most cases. If it appears to have a negative impact on specific scenarios, the impact remains very small and memoization can be removed in that case.

Find out more here: [https://stackoverflow.com/a/63405621/4053349](https://stackoverflow.com/a/63405621/4053349)

For this reason, all generated components are wrapped into `memo()`.

### Interfaces

All properties exposed by the component for overrides are listed in the component `Props`’ interface. Please refer to the [instances article](instances.md) for more details about the overrides.

### Named exports

All components use named exports. While many examples on Internet use default exports, named exports have more benefits, e.g. in terms of usage (auto-import, auto-completion from IDEs) and performance (considering ES6 modules and tree shaking).

### Variable name and function name

```tsx
export const Card: FC<Props> = memo(function Card(props = {}) {
  // ...
}
```

`Card` is defined twice: as the exported variable name and the inner function.

* The exported variable is required for named exports.
* The inner function is named (instead of anonymous) to name the component function, which helps showing better stack traces when debugging. This practice is enforced by the ESLint config included in the project.

### Annotation @figmaId

This annotation is added in a comment above the component. Please leave it as it is. In an incoming release, we will use it to map a coded component to the corresponding Figma node, e.g. for updates.
