By bgolus

Basic rendering:
Take a single mesh. Upload mesh data to the GPU once at startup. Every frame set the shader to use, upload all of the material data, and call Draw(). Rinse and repeat for every object.
Benefits: Works on literally every GPU ever made, and is extremely flexible. Unity does some work to try to not change the shader or material data if it doesn't have to, so if two meshes use the exact same material & shader variant it'll sometimes only update the position data and render those meshes one after another.

Dynamic batching:
Take several meshes with very low poly counts and exactly the same material & shader variant and combine into a single mesh, every single update. Send that mesh data to the GPU, set the shader & material data for that single material, call Draw() once. Done.
Benefits: Very, very fast on the GPU, even with the cost of uploading a new mesh every frame as it's only rendering a single "thing". Dynamic batching is limited to very simple meshes so this usually isn't a ton of data. Particle systems work like this too. Main cost comes from the CPU combing meshes. Limited per object data can be stored in the mesh vertex data.

Static batching:
Take several different meshes with exactly the same material into a single mesh once during build time / play mode startup. Upload that data to the GPU once on startup. Set the shader variant & material data for that single material, call DrawIndexed() for each renderer component as an offset & range of triangle indices. Done.
Benefits: Very fast on the CPU & GPU, but uses a lot of memory and is, well, static. Is quite flexible in terms of allowing individual renderer components to be hidden for occlusion, LOD, or via script. Unity will also swap the shader variant and data for things like dynamic lights & shadows so only the renderer components that are affected needs to be rendered again rather than the whole batched mesh, but that incurs some cost in doing that swap. Per object data can be stored in the mesh vertex data.

GPU Instancing:
Gather up data from several identical meshes with exactly the same material & shader variant. Upload mesh data to the GPU once at startup. Put all of the unique-per-instance data into arrays that can be indexed by instance ID. For basic instancing that's the object to world matrices only. For more complex setups that can be additional arbitrary instanced data, like a color, or UV offsets, etc. (no textures). Those arrays can be constructed manually via script for when calling DrawMeshInstanced, or set on renderer components using a MaterialPropertyBlock, that later of which Unity will put into arrays for you internally.
Benefits: Very fast on the CPU to render a lot of the same object. Actually a bit slower on the GPU due to the indexed data look up happening in the shader, but overall faster because usually when drawing a few thousand of something often the GPU is sitting idle waiting for the CPU to tell it what to render next so the additional GPU cost is hidden.

SRP Batcher:
Gather up data from several different meshes with the same shader. Upload mesh data once at startup. Put per-material data into long lists and upload once at startup*. Put per-object data into long lists and upload every frame. Render each mesh by setting the offsets to the list data and using a Draw().
Benefits: Much less data being uploaded between each draw and much less communication between the CPU and GPU. Unlike traditional rendering switching between different sets of material data is essentially free as the data is already uploaded.

[source](https://forum.unity.com/threads/srp-batcher-and-gpu-instancing.833362/)

other references
https://mathmakeworld.tistory.com/61