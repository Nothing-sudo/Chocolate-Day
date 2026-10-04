## 2026-10-04 - Static WebGL Buffer Reuse in Render Loop
**Learning:** In WebGL applications, calling `gl.createBuffer()` and `gl.bufferData()` inside utility render helpers like `blit()` creates tens of buffer objects and typed array allocations per frame (16+ times per frame at 60 FPS), causing severe GC pressure and GPU memory thrashing.
**Action:** Always allocate and initialize static quad vertex and index buffers once during WebGL context setup and reuse them across all `blit()` draw calls.
