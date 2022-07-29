# Introduction

**Clapy** is a [Figma plugin](https://www.figma.com/community/plugin/1083031796594968801) allowing you to generate React components from your Figma designs.

Here is a quick demo:

{% embed url="https://www.youtube.com/watch?v=J4u2uuJdT-A" %}
Quick demo of Clapy, the Figma-to-code generator
{% endembed %}

Our goal is to accelerate the development of React-based web applications, especially front-end integrations.

We created Clapy because, as developers, we know how time consuming pixel-perfecting a UI is, while there is so much more to code in a web app. What's worse than slowly translating a Figma file to code with 3 screens? Figma for reference, the IDE to code and the browser to preview? 🙄

With its developer-centric features, Clapy can be used for following use cases:

1. Kickstart a web app from Figma
2. Automate the integration of your wireframe and updates
3. Automate your Design System management

### Options

Before generating the code, you have a couple of options.

#### Export as full width/height



#### Full width/height

If enabled, the selected element will be stretched to use all width and height available, even if "Fill container" is not configured. Useful for top-level frames. If generating a page, this is likely the expected behavior.

#### Download as zip

If enabled, the code is downloaded as zip file instead of being sent to CodeSandbox for preview.

The project uses ViteJS for crazy fast development builds.

#### SCSS instead of CSS (beta)

If enabled, styles will be written in .scss files instead of .css.

#### Indent classes with BEM convention

If enabled, the generated SCSS is a tree of classes following the BEM convention instead of top-level classes only. For now, only components can follow this convention. Instance overrides are still at the root.

CSS modules make most of BEM obsolete, but it is useful for legacy projects.
