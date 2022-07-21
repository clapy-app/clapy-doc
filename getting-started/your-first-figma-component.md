# Your first Figma component

If you already have a Figma design, you can skip this section and directly head to the next one: [Generate code with Clapy](generate-code-with-clapy.md).

If you don't have Figma designs yet, this sections helps you setup your first design, ready to be converted into code with Clapy.

### The basics <a href="#the-basics" id="the-basics"></a>

The first step is to create a [Figma account](https://www.figma.com/) and open their application. You can use the web app or the desktop app.

Once Figma is opened, create a `New design file`.

![Its easy to create our first design file with Figma](https://697176422-files.gitbook.io/\~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FyY2FYmE8uVvtJoajeXom%2Fuploads%2FxI2J0gSgnNQEhKXM3Z1L%2Fimage.png?alt=media\&token=b9c091ac-9fc9-4531-8d63-69b6abcf510e)

After you have successfully created your design file, it is time to create your first frame.

{% hint style="info" %}
It is important for Clapy that we use **frames** instead of **rectangles** as containers, to generate high quality code.

For background colors, use the `fill` property of your frames.

Rectangles should only be used in specific cases where that's the shape you want for a drawing.
{% endhint %}

![Creating our first frame](https://697176422-files.gitbook.io/\~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FyY2FYmE8uVvtJoajeXom%2Fuploads%2FGqEWcgzQmdYYOEWnuupP%2F0632817b18cc1ea67a9f1d1dfab020a6.gif?alt=media\&token=02e282f8-94b5-40a0-a1db-4e48294832e3)

Awesome, we've got the right setup to get started. To continue, add a `Text` in the frame you've just created.

![Writing some text](https://697176422-files.gitbook.io/\~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FyY2FYmE8uVvtJoajeXom%2Fuploads%2F1rJ3782Nhbq8L6yB6RWZ%2F755a68198ec3f9cf052e8c5436606010.gif?alt=media\&token=e2984495-a4b1-4202-a402-c63944798aba)

### The layout

Very well. Now that we've got our text, let's define the layout. Select your text, right-click, then choose "Add auto layout" (or you can use the shortcut: `SHIFT + A`).

The text is now wrapped into a sub-frame using the auto layout.

{% hint style="info" %}
**Good to know:** Using auto layout is generally a good practice, especially to get clean code with Clapy.

You can find a presentation here: [https://www.youtube.com/watch?v=TyaGpGDFczw](https://www.youtube.com/watch?v=TyaGpGDFczw)

and a playground here: [https://www.figma.com/community/file/784448220678228461](https://www.figma.com/community/file/784448220678228461)
{% endhint %}

### Let's style it a bit

Now we are ready to give our button a color. You can do this by selecting your frame and going over to the right to see the properties panel. Here, you can select the `fill` and give your button a color.

![Giving our button a color](https://697176422-files.gitbook.io/\~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FyY2FYmE8uVvtJoajeXom%2Fuploads%2FcwMduqFRuV82h6TLFv3b%2Fimage.png?alt=media\&token=853ee3f1-e027-4f77-a6b2-858811bf78c7)

Awesome, we are almost done! Select your frame and look at the properties panel again. You will see something called `Auto layout`. You will see some properties with default values, e.g. `10` for the padding. We can adjust these by clicking when the arrow cursor appears and dragging horizontally.

![Adding padding to our button](https://697176422-files.gitbook.io/\~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FyY2FYmE8uVvtJoajeXom%2Fuploads%2Fui9pXdfWNrYFD2Yqedyj%2F4ed5a64da662a2dad1835d5fe947315c.gif?alt=media\&token=ec2abcaf-863e-4bab-aa1f-0e674dbaf51c)

Wow, that went very well! Our last step is to make our outer frame an auto layout as well. We can do this by selecting it and pressing `SHIFT + A` (or right-click > `Add auto layout`).

We can now adjust the properties a bit. In the `Auto layout` section, a table with 9 cells represent the vertical and horizontal alignment of the selection's children. Select the middle one.

![Selecting center alignment of our auto layout](https://697176422-files.gitbook.io/\~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FyY2FYmE8uVvtJoajeXom%2Fuploads%2FNkj8PDXKJ88Ynx2FE0Ki%2F9fa6df2a4af155b06e082927af8f5c12.gif?alt=media\&token=3b725186-0464-41c3-9614-ca833a02b7f5)

We are almost done! Select your outer frame again, and you will see at the top of your properties panel the `width` and `height` of your frame. Set the `width` from `hug` to `fixed.`

Awesome. Finally, right-click on your button and click `Create component`. And thats all!

Congratulations! We've created our first component, [ready to be turned into code by Clapy](generate-code-with-clapy.md). 🥳

