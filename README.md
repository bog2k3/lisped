# lisped
Lisped is a Linear Space Photo Editor which performs all operations in un-gamma-corrected space.
It has nothing to do with the lisp programming language, it's written in C++.

## Why lisped?
I have been searching high and low for a photo editor that handles color and tones correctly and found none. Not even Gimp or Photoshop do this right (newest versions of Photoshop have some options for gamma-correct blending, though they're not complete).

## What linear space or gamma-correct color handling means? 
Well, this subject is quite big and is well covered in this article: https://blog.johnnovak.net/2016/09/21/what-every-coder-should-know-about-gamma/

TLDR; photos and digital art are usually created for display on a computer/table/phone screen which have a non-linear response to input (twice the value of a pixel doesn't make twice as much light) and for this reason the images are intrinsically gamma-corrected which means the pixel values of the images is mapped non-linearly to the actual light value that hit the camera sensor.

This is not an issue when displaying the pictures, but when editing them, blending elements together and altering the colors and tones via curves, levels, saturation etc, the results are often wrong.

Have you ever noticed how when pulling up the curves on an image to lighten it up, the saturation is also increased? This is one of the problems with working in non-linear space. Another one is when blending images together.


This project aims to provide a tool for working with photos and adjusting them in linear space in order to easily obtain the desired results without wierd side-effects.

## How does this work?
When loading a photo, lisped converts its internal representation from gamma-corrected space back into linear space and performs all adjustments on this data. Then, when rendering the picture to the screen (or when exporting the file) gamma-correction is reapplied on the fly to make it look as it should on the computer display.
