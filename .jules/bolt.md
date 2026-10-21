## 2026-10-21 - WebGL Static Geometry Buffer Reuse in Blit Pass
**Learning:** `gl.createBuffer()` and `gl.bufferData()` inside frequent utility draw passes (such as `blit()`) create heavy CPU-GPU memory allocation churn (~1,800 buffer allocations/sec at 60 FPS). Static quad geometry buffers should be created once on context initialization and bound before drawing.
**Action:** Always pre-allocate static full-screen quad vertex and index buffers globally or on render context init rather than creating transient buffers within render helper functions.
