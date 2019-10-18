# Spiderverse-Styled-Rendering

## Alpha Progress:

So far two main features have been fully implemented -- Toon Shading and Chromatic Abberation!

![](Images/shaderShot.PNG)

These post process effects are done as separate shaders in Unreal, implemented as Unreal Materials.  GLSL code, in Unreal Engine read as a .usf file, can be linked to a node in Unreal's Blueprints to make this post process material:

![](Images/shaderNode.PNG)

These separate shaders can be ran one-by-one in an array within a Post Process Volume instance in the scene:

![](Images/shaderArray.PNG)

The next steps are finishing outline drawing, smearing effects, and comic book style textures!
