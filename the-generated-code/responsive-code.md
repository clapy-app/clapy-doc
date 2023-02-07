# Responsive code

By default, the generated code is as responsive as it is in Figma, i.e. if you use the auto layout and constraints in Figma settings, the code equivalent will be generated.

To check if your design is responsive, the first thing you can try is to **resize it in Figma** and see what happens. Looks good? Your design should be ready!

Another aspect of the responsiveness is the ability to switch from a desktop design to a mobile design if the device screen is small enough. Figma doesn't support it natively. What people typically do is to prepare 2 separate designs: one for desktop, another for mobile (sometimes more than 2 designs).

In the code, you can rely on a CSS rule, _media queries_, to operate this switch automatically. While generating the media queries is not automated by Clapy (yet), you can follow these steps to add them manually:

* Group the 2 designs in a parent frame, ideally auto-layout (e.g. horizontal).
* Generate the code selecting the parent frame. In the generated code, you will have the 2 views rendered next to each other.
* In the generated code, you will find the 2 components rendered next to each other. Ensure each component has a className you can use.
* Add CSS with media queries to render the right block, something like:

```css
.desktopView { display: flex; }
.mobileView { display: none; }

@media (max-width: 768px) {
  .desktopView { display: none; }
  .mobileView { display: flex; }
}
```

Once the media queries take effect, it should render the component matching the screen size, giving a responsive effect.

The same technique applies to 3 or more screen sizes, if required.
