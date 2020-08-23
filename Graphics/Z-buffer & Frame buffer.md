By Daniel Rauer

The frame buffer is a block of video memory from which the screen reads. It is usually stored at 32 bits per pixel, representing RGBA. Only the alpha channel has no direct effect on what you see on your monitor. It is usually cleared at the beginning of each frame (you can set this on your Camera), and then everything in your scene is rendered into that buffer.

The Z buffer is 16-32 bits per pixel, and stores a single depth value for each pixel. Almost every shader should use Z testing, otherwise you can get objects appearing in front of things that they should be behind. Transparent objects tend not to write to the Z buffer, because sorting transparent rendering is generally a more difficult problem than the Z buffer solves.

Render queues are used to change the order in which things render within a given frame. This ability is used for things like forcing the draw order of specific transparent objects.

[source](https://forum.unity.com/threads/z-buffers-and-framebuffers.152881/)