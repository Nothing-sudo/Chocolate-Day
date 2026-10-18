## 2026-10-18 - WebGL Static Geometry Buffer Reuse in Render Loop
**Learning:** Calling `gl.createBuffer()` and `gl.bufferData()` within every pass of a WebGL rendering loop causes significant GPU buffer allocation overhead, TypedArray GC pressure, and unnecessary CPU-to-GPU data transfers across 15+ render passes per frame.
**Action:** Extract full-screen quad vertex and element buffer creation/data uploads into a single initialization routine (`initBlit()`) and bind/draw the pre-allocated buffers inside `blit()`.
