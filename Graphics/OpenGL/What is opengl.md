By Chrerno

Nvidia, AMD, and Itel they all support OpenGL as a rendering API so what we need to now is not really rely on Windows.
OpenGL 1.1 was kind of the first real version of OpenGL.
Since we're on Windows, we need a way to actually get all of the modern OpenGL functions.
If we want to actually call those functions in C++ code, we need to get them from somewhere.
OpenGL functions, it's not something you download really. it's stuff that is actually in your graphics drivers.
the OpenGL functions are implemented in your GPU drivers.
GLEW lets us access functions