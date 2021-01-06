By Ben Cook

What is the Rendering Pipeline?
 - The Rendering Pipeline is a series of stages that take place in order to render an image to the screen.
 - Four stages are programmable via "Shaders".
 - Shaders are pieces of code written in GLSL (OpenGL Shading Language), or HLSL (High-Level Shading Language) if you're using Direct3D.
 - GLSL is based on C.

------------------------------
The Rendering Pipeline Stages
 1. Vertex Specification
 2. Vertex Shader (programmable)
 3. Tessellation (programmable)
 4. Geometry Shader (programmable)
 5. Vertex Post-Processing
 6. Primitive Assembly
 7. Rasterization
 8. Fragment Shader (programmable)
 9. PerSample Operations
------------------------------
1. Vertex Specification
 - A vertex (plural: vertices) is a point in space, usually defined with x, y and z co-oricates.
 - A primitive is a simple shape defined using one or more vertices.
 - Usually we use triangles, but we can also use points, lines and quads.
 - Vertex Specification: Setting up the data of the vertices for the primitives we want to render.
 - Done in the application itself.
 - Uses VAOs (Vertex Array Objects) and VBOs (Vertex Buffer Objects).
 - VAO defined WHAT data a vertex has (position, color, texture, normals, etc)
 - VBO defines the data itself 
    - so you could have multiple VBOs are attached to a VAO
 - Attribute Pointers define where and how shaders can access vertex data.
 - Creating VAO/VBO
  1. Generate a VAO ID.
  2. Bind the VAO with that ID.
  3. Generate a VBO ID.
  4. Bind the VBO with that ID (now you're working on the chosen VBO attached to the chosen VAO).
  5. Attach the vertex data to that VBO.
  6. Define the Attribute Pointer formatting.
  7. Enable the Attribute Pointer.
  8. Unbind the VAO and VBO ready for the next object to be bound.
 - Initiating Draw
  1. Activate Shader Program you want to use
  2. Bind VAO of object you want to draw
  3. Call glDrawArrays, which initiates the rest of the pipeline
------------------------------
2. Vertex Shader
 - Handles vertices individually
 - NOT optional
 - MUST store something in gl-Position as it is used by later stages
 - Can specify additional outputs that can be picked up and used by user-defined shaders later in pipeline
 - Inputs consist of the vertex data itself.
 - Simple Example
```c++
#version 330

layout (location = 0) in vec3 pos;

void main()
{
    gl_Position = vec4(pos, 1.0);
}
```
------------------------------
3. Tessellation
 - Allows you to divide up data in to smaller primitives. (if you are using quads you could potentially divided up into two triangles)
    - Even if you feed OpenGL quads, the triangularization is done by the driver on the CPU side before it even hits the GPU. Modern GPUs these days eat nothing except triangles. (Well, and lines and points.) So something will be triangulating, whether it's you or the driver -- it doesn't matter too much where it happens.[source](https://stackoverflow.com/questions/14555446/opengl-is-it-more-efficient-to-use-gl-quads-or-gl-triangles)
    - A lot of games use it for the graphics in things like oceans for like water the constantly moving
 - Relatively new shader type, appeared in OpenGL 4.0.
 - Can be used to add higher levels of detail dynamically.
------------------------------
4. Geometry Shader
 - Vertex Shader handles vertices, Geometry Shader handles primitives (group of vertices).
 - Takes primitives then "emits" their vertices to create the given primitive, or even new primitives.
 - Can alter data given to it to modify given primitives, or even create new ones.
 - Can even alter the primitive type (points, lines, triangles, etc).
------------------------------
5. Vertex Post-Processing
 - Transform Feedback (if enabled)
    - Result of vertex and Geometry stages saved to buffers for later use
 - Clipping
    - Primitives that won't be visible are removed (don't want to draw things we can't see!)
    - Positions converted from "clip-space" to "window space" (more on this later)
------------------------------
6. Primitive Assembly
 - Vertices are converted in to a series of primitives.
 - So if rendering triangles... 6 vertices would become 2 triangles (3 vertices each)
 - Face culling
    - Face culling is the removal of primitives that can't be seen, or are facing away from the viewer. We don't want to draw something if we can't see it!
    - Removing the opposite side that we can't see
------------------------------
7. Rasterization
 - Converts primitives in to "Fragments".
 - Fragments are pieces of data for each pixel, obtained from the resterization process.
 - Fragment data will be interpolated based on its position relative to each vertex.
------------------------------
8. Fragment Shader
 - Handles data for each fragment.
 - Is optional but it's rare to not use it. Exceptions are cases where only depth or stencil data is required (more on depth data later).
 - Most important output is the color of the pixel that the fragment covers.
 - Simplest OpenGL programs usually have a Vertex Shader and a Fragment Shader.
 - Simple Example
```c++
#version 330

out vec4 color;

void main()
{
    color = vec4(1.0, 0.0, 0.0, 1.0);
}
```
------------------------------