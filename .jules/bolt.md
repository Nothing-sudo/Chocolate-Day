## 2026-10-16 - Pre-allocate static WebGL geometry buffers
**Learning:** Calling `gl.createBuffer()` and `gl.bufferData()` inside `blit()` during `requestAnimationFrame` creates hundreds of GPU allocations per second, leading to frame drops, driver overhead, and garbage collection stutter.
**Action:** Always pre-allocate static vertex and index buffers once during context initialization and bind/reuse them inside render loops.
