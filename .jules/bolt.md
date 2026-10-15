## 2024-10-15 - Reuse WebGL Geometry Buffers in Render Loop
**Learning:** Reallocating WebGL buffers (`gl.createBuffer()`) and buffering static vertex/element data (`gl.bufferData()`) on every frame in `blit()` creates unnecessary CPU heap allocations, garbage collection pressure, and driver overhead when called 17+ times per frame.
**Action:** Create and upload full-screen quad vertex and index buffers once during WebGL initialization and reuse them inside `blit()` during the animation render loop.
