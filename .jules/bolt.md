## 2026-08-26 - WebGL Quad Buffer Allocation in Render Loops
**Learning:** Calling `gl.createBuffer()` and `gl.bufferData()` inside helper functions like `blit()` that execute repeatedly per frame causes massive CPU heap allocations, GPU memory churn, and garbage collection pauses.
**Action:** Always pre-allocate static geometry buffers (like full-screen quad vertex and index buffers) during WebGL initialization and bind/reuse them inside the draw/blit loop.
