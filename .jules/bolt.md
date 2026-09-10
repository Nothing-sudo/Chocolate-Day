## 2026-09-10 - WebGL Static Quad Buffer Allocation in Render Loop
**Learning:** Calling `gl.createBuffer()` and `gl.bufferData()` inside the WebGL render loop (`blit()`) causes significant CPU/GPU memory allocation churn and garbage collection pauses across frames.
**Action:** Always allocate static WebGL buffers (such as full-screen quad vertex and index buffers) once during initialization and reuse them inside render loop functions.
