By bgolus

AlphaTest is an opaque queue, like Geometry, Background, and any queue 0 through 2500. Opaque queues are rendered in front to back order.

Transparent is a, well, transparent queue, along with Overlay and all queues after 2500. Transparent queues are sorted back to front.

Front to back sorting means the objects closest to the camera are rendered first with objects far away rendering last. This is done actually specifically for the reason your shader is working like you expect, which is ZTest is rejecting pixels where the depth has already been written to.

Back to front sorting is as you can likely guess there opposite with objects furthest from the camera rendered first and objects closest to the camera rendered last. This is because it's expected that these objects will not have the benefit of the depth buffer for sorting and can be seen through each other so you don't want ZTest rejecting pixels anyway.

[source](https://forum.unity.com/threads/difference-between-alphatest-and-transparent-renderqueue.458750/)