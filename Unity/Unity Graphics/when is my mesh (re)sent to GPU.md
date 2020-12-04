By LennartJohansen

Every frame your mesh is rendered it will make a drawcall. If you have changed the mesh on the CPU or it is the first frame it is used it will in addition to this upload the mesh to the GPU.
This drawcall will happen on each frame even if you do not change the transform or any other setting on the Mesh.

in some cases systems like dynamic batching, instancing etc will manage to render multiple similar meshes as a single drawcall.

Shadows, multiple lights(Forward), projectors etc will create additional drawcalls as these will render the mesh again to create effects.

By aleksandrk

If geometry would get uploaded each frame, the performance would've been horrible.
The geometry gets uploaded to the GPU only if it changes.

[source](https://forum.unity.com/threads/when-is-my-mesh-re-sent-to-gpu-need-to-optimize-with-compute-buffer.683989/)