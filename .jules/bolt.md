## 2026-10-20 - Reuse Static WebGL Quad Geometry Buffers Across Frames
**Learning:** In WebGL render loops, calling `gl.createBuffer()` and allocating new TypedArrays inside a `blit()` function invoked multiple times per frame (e.g., 15 times/frame for fluid solvers) creates massive garbage collection churn, GPU memory leaks, and CPU-to-GPU bandwidth bottlenecks (~900 allocations/sec at 60 FPS).
**Action:** Always pre-allocate static geometry buffers (such as full-screen quad vertex and index buffers) during WebGL context setup, and simply bind and draw with them inside the render/blit loop.
