## 2026-10-01 - Avoid Per-Frame WebGL Buffer Allocation

**Learning:** Allocating WebGL buffers (`gl.createBuffer()`) and transferring data (`gl.bufferData()`) inside helper functions called multiple times per frame (like `blit()`) creates severe allocation churn, GC pauses, and CPU-to-GPU overhead. Static geometry buffers (e.g. full-screen quads) should be initialized once and reused.
**Action:** Always pre-allocate static vertex and index buffers during WebGL context initialization and re-bind existing buffer objects inside rendering loops.
