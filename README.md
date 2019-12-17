# Spiderverse-Styled-Rendering

## Alpha Progress:

So far two main features have been fully implemented -- Toon Shading and Chromatic Abberation!  The Toon Shading has 5 bands of color and differentiates based on the original color's luminance.  The Chromatic Abberation scales to be more intense the further away the camera is from an object.

![](Images/shaderShot.PNG)

These post process effects are done as separate shaders in Unreal, implemented as Unreal Materials.  GLSL code, in Unreal Engine read as a .usf file, can be linked to a node in Unreal's Blueprints to make this post process material:

![](Images/shaderNode.PNG)

These separate shaders can be ran one-by-one in an array within a Post Process Volume instance in the scene:

![](Images/shaderArray.PNG)

The next steps are finishing outline drawing, smearing effects, and comic book style textures!

## Beta Progress

Now includes Ben-Day textures and outlining!


Currently, outlining involves coloring in outlines when the dot product between the camera vector and the geometry's surface normal is underneath a particular value.  This creates a decent outline, but it is not ideal as the line quality can be a bit inconsistent and doesn't scale nicely when zoomed out from an object.  Next steps are to try using a depth channel to further tune the outline drawing, and perhaps look into silhouette rendering.
![](Images/outlineTry1.PNG)

Ben-day Dot texturing is done by generating a grid of an adjustable size and drawing dots within the grid cells.  These dots shade the image with a darker tone from the original image to create the impression of the iconic comic book dots.  The dots' radii increase within darker tones, and eventually do not appear in the lightest tones of the image.  It also happens to pair very well with the outlining!
![](Images/bendaydots.PNG)
![](Images/bendaydots_close.PNG)

## Final Progress

![](Images/betaShot1.PNG)

Outlining has been reworked to incorporate both the normal and depth buffer.  Neighboring pixels are sampled in an X shape around the current pixel of the screen texture.
Chromatic Aberration was also edited to be a bit less intense, and scale better with distance.
Ben-Day dot bug where dots did not scale based on screen resolution was fixed, so now dots are more uniformly circular.  Printing artifacts that separate dots by the screen texture's CMYK value are produced by offsetting the dots based on the color value.

Here is each filter applied in order:

Default Render
![](Images/betaProcess1.PNG)
Toon Shading
![](Images/betaProcess2.PNG)
Ben-Day Dots
![](Images/betaProcess3.PNG)
Chromatic Aberration
![](Images/betaProcess4.PNG)
Outlining
![](Images/betaProcess5.PNG)

<hr>

## Resources
- [Unreal Engine 4 Custom Shaders Tutorial](https://www.raywenderlich.com/57-unreal-engine-4-custom-shaders-tutorial)
- [GLSL Toon Shading in Unity](https://en.wikibooks.org/wiki/GLSL_Programming/Unity/Toon_Shading)
- [WebGL Halftone Shader](http://webstaff.itn.liu.se/~stegu/OpenGLinsights/shadertutorial.html)
- [Unity Outline Shader](https://roystan.net/articles/outline-shader.html)
- [Pixar Toon Shading (Outline Thickness)](https://graphics.pixar.com/library/ToonRendering/paper.pdf)
- [Super Hero 3D Model](https://free3d.com/3d-model/fig-superherocape-v3--246988.html)

