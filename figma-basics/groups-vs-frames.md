---
description: >-
  Let's be honest: the distinction between "groups" and "frames" in Figma can be
  confusing. This quick guide should help you better identify when to use groups
  instead of frames.
---

# Groups vs Frames

New users in Figma tend to use groups instead of frames to, well, group elements together.&#x20;

But in most cases, the expected behavior by the designer is to start defining the **layout** of the elements, which is better handled by frames.



Here's a 3min video to help you understand in which cases groups are better than frames.

{% hint style="info" %}
**SPOIL ALERT**: in 99% cases, you get better results with frames than with groups. 😋&#x20;
{% endhint %}

{% embed url="https://youtu.be/UVx33W_Bzu4" %}
Quick groups vs frame tutorial by VisualSpicer.
{% endembed %}



### What's the impact in the code?

In Clapy, groups and frames are not converted using the same principles, because they typically don't convey the same concepts in th code:

* Frames are the closest representation of a \<div> in a 2D design file.\
  \-> if you wrap elements in a frame, this frame will be converted to a \<div> in the code.
* Groups can be used to create complex designs, that can be converted to .svg files.\
  \-> if you wrap elements in a group, this group will be exported as a static .svg file.



### Our recommendation for better code with Clapy

Frames are a lot more powerful than groups, since they handle the layout with constraints, especially with the underrated feature of ["auto-layout"](add-auto-layout-in-frames.md).&#x20;

They should thus be your default "go to" when it comes to wrapping elements together.

