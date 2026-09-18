## 2026-09-18 - Avoid Buffer Re-allocation in WebGL Render Loop

**Learning:** Re-creating WebGL buffers (`gl.createBuffer()`) and uploading data (`gl.bufferData()`) inside a rendering loop step (`blit()`) causes significant CPU-GPU overhead, garbage collection pressure, and driver memory thrashing, especially when `blit()` is invoked 15+ times per frame.
**Action:** Always allocate static WebGL geometry buffers (e.g., quad vertex and index buffers) once during initialization and reuse them across frame renders.
