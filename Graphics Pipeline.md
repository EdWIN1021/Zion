- Takes as input a set of 3D coordinates and transforms these to colored 2D pixels on the screen
- The graphics pipeline can be divided into several steps where each step requires the output of the previous step as its input
- The processing cores run small programs on the GPU for each step of the pipeline (shaders)
- Shaders are written in the OpenGL Shading Language (GLSL)



## Vertex Shader
- The main purpose of the vertex shader is to transform 3D coordinates into different 3D coordinates


## Geometry Shader
- The geometry shader takes as input a collection of vertices that form a primitive and has the ability to generate other shapes by emitting new vertices to form new (or other) primitive(s). (原本输入可能是一个三角形，GS 可以输出一个更复杂的几何体，甚至多个三角形) 

## Primitive Sssembly
- takes as input all the vertices (or vertex if GL_POINTS is chosen) from the vertex (or geometry) shader that form one or more primitives and assembles all the point(s) in the primitive shape given

## Rasterization Stage
- maps the resulting primitive(s) to the corresponding pixels on the final screen, resulting in fragments for the fragment shader to use.

##  Clipping
- Clipping discards all fragments that are outside your view, increasing performance

## Fragment Shader
- calculate the final color of a pixel and this is usually the stage where all the advanced OpenGL effects occur
-  Usually the fragment shader contains data about the 3D scene that it can use to calculate the final pixel color (like lights, shadows, color of the light and so on

## Alpha Test and Blending Stage
- This stage checks the corresponding depth (and stencil) value of the fragment and uses those to check if the resulting fragment is in front or behind other objects and should be discarded accordingly.
- The stage also checks for alpha values (alpha values define the opacity of an object) and blends (混合就是按透明度把新颜色和原有颜色组合起来，让半透明物体显示正确效果) the objects accordingly.


tessellation stage
transform feedback loop