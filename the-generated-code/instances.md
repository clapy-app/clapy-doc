---
description: >-
  This article describes the generated code for instances of components, how
  overrides are applied and the principles we follow.
---

# Instances

{% hint style="info" %}
Any question about the design decisions? Anything not matching your project practices? [Please let us know](https://clapy.co/contact)! we may add an option for the flexibility you need.
{% endhint %}

At Clapy, we are proud to be the first tool generating code from Figma with instances of components and overrides. We consider customizable components to be the bottom line of production-ready code.

### Overrides

If a frame contains multiple instances of a Button component, with customizations done on some of them (color, text…), we generate a single Button component. Instances refer to this component, passing properties that apply the customizations, we call _overrides_ in this article.

Figma allows 4 different overrides:

* Styles (fill, stroke, layout…)
* Text
* Swap instances
* Show or hide

All those overrides are passed to the instance as properties.

### Styles

The style changes are applied with classes. The system is inspired by [MUI](https://mui.com/): the className property applies to the root node, and sub-nodes are restyled using a `classes` property. Classes are passed down to the target node.

Example:

```tsx
interface Props {
  className?: string;
  classes?: {
    root?: string;
    btnTxt?: string;
  };
}
export const Button: FC<Props> = memo(function Button(props = {}) {
  return (
    <button className={`${classes.root} ${props.classes?.root || ''} ${props.className || ''}`}>
      <div className={props.classes?.btnTxt}>Click</div>
    </button>
  );
});
```

Usage:

```tsx
<Button
  className={classes.newRoot}
  classes={{
    btnTxt: classes.newTextStyle
  }} />
```

#### CSS selector specificity

To ensure instance styles override the component styles, the instance selectors are doubled. Example:

```css
.label.label {
  /* ... */
}
```

We opted for this solution because we use CSS modules. A downside of it is that, in the selector, we cannot refer to classes defined in a separate file.

#### `className` and the `root` override

The root node can be overridden with both `className` and `classes.root`. This is an inspiration from MUI, with the benefits:

* Developers are used to the `className` property that would apply their style to the parent node,
* Not being able to override the root node inside `classes` would be weird, so we keep it for consistency.

### Text

If the text changes in an instance, the whole new text is passed as a property (`text`). Figma gives a lot of flexibility on what can be changed in the text. We keep this flexibility in the generated code.

Example:

```tsx
interface Props {
  text?: {
    btnTxt?: ReactNode;
  };
}
export const Button: FC<Props> = memo(function Button(props = {}) {
  return (
    <button>
      {props.text?.btnTxt != null
        ? props.text?.btnTxt
        : <div className={classes.btnTxt}>Click me!</div>}
    </button>
  );
});
```

Usage:

```tsx
<Button text={{
  btnTxt: <div className={classes.newTxtStyle}>New text</div>
}} />
```

### Swap instances

This refers to a Figma feature: replace an instance of component A with an instance of component B, putting it where the instance of A was, even if it’s inside another instance.

In React, we use [render props](https://reactjs.org/docs/render-props.html) to replicate this behavior, i.e. instances of sub-components passed as properties to apply the `swap`.

{% hint style="info" %}
This feature is particularly interesting in Figma when you have an instance containing other instances. The latter can be swapped with your own components to to put arbitrary content in the original component.
{% endhint %}

Example:

```tsx
interface Props {
  swap?: {
    btnArrow?: ReactNode;
  };
}
export const Button: FC<Props> = memo(function Button(props = {}) {
  return (
    <button>
      {props.swap?.btnArrow || <ArrowComponent />}
      <div className={classes.btnTxt}>Click me!</div>
    </button>
  );
});
```

Usage:

```tsx
<Button swap={{
  btnArrow: <StarComponent />
}} />
```

### Show or hide

An instance can reveal a node that is hidden in the original component, or on the contrary, hide a node that is visible. The `hide` property applies the override.

Example:

```tsx
interface Props {
  hide?: {
    btnArrow?: boolean;
  };
}
export const Button: FC<Props> = memo(function Button(props = {}) {
  return (
    <button>
      {!props.hide?.btnArrow && <ArrowComponent />}
      <div className={classes.btnTxt}>Click me!</div>
    </button>
  );
});
```

Usage:

```tsx
<Button hide={{
  btnArrow: true
}} />
```

### Special case: SVG

When a Figma node exported as SVG is customized in an instance, Clapy exports the new SVG with overrides, and pass it to the instance leveraging the _swap_ feature described above (render prop).

### Sub-instances

In case you wonder, we support sub-instances (instances containing instances). And as many layers of components as you wish.

### The list of properties

In short, you should design on Figma showing examples of usages. E.g. if a list entry is supposed to have a dynamic texts, you should add 2+ entries with different texts.

Clapy will guess the properties from your examples.

{% hint style="info" %}
Anything incorrect in the list of properties generated by Clapy? [Please let us know](https://clapy.co/contact)!
{% endhint %}

