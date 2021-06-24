1. VBO
- A Vertex Buffer Object (VBO) is the common term for a normal Buffer Object when it is used as a source for vertex array data. It is no different from any other buffer object, and a buffer object used for Transform Feedback or asynchronous pixel transfers can be used as source values for vertex arrays.
[source](https://www.khronos.org/opengl/wiki/Vertex_Specification#Vertex_Array_Object)

2. VAO
- A Vertex Array Object (VAO) is an OpenGL Object that stores all of the state needed to supply vertex data (with one minor exception noted below). It stores the format of the vertex data as well as the Buffer Objects (see below) providing the vertex data arrays. Note that VAOs do not copy, freeze or store the contents of the referenced buffers - if you change any of the data in the buffers referenced by an existing VAO, those changes will be seen by users of the VAO.
[source](https://www.khronos.org/opengl/wiki/Vertex_Specification#Vertex_Array_Object)
- When you bind a VAO, you are binding an object that stores the state used for vertex arrays. When you call a function that modifies the state for vertex arrays, that function will modify the state stored in the VAO currently bound. When you render, the rendering system will use the vertex array state found in the currently bound VAO.
[source](https://computergraphics.stackexchange.com/questions/10332/understanding-vao-and-vbo)