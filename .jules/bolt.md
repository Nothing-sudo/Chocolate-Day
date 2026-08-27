## 2026-08-27 - Reuse static WebGL buffers in frame loop
**Learning:** In WebGL simulation frame loops, allocating new vertex/index buffers and re-uploading buffer data inside functions like `blit()` on every pass creates heavy GPU re-allocation and CPU garbage collection churn (~15+ allocations/frame).
**Action:** Always pre-allocate static geometry (quads) once during context initialization and bind the static buffer objects inside the rendering loop.
