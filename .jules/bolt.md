## 2025-02-03 - WebGL Buffer Allocation Anti-Pattern in Render Loop
**Learning:** In WebGL render loops, calling `gl.createBuffer()` and `gl.bufferData()` within reusable drawing helpers like `blit()` creates multiple GPU buffers and TypedArrays per draw call (~16 calls/frame = ~1,920 allocations/sec at 60 FPS). This causes heavy GC pressure and GPU driver overhead.
**Action:** Always allocate static WebGL geometry buffers (vertex, index) once during setup before any draw calls (such as in `initFBOs()` or startup) and bind them in `blit()`.
