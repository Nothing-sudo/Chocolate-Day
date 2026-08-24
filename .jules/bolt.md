## 2026-08-24 - Avoid Creating WebGL Geometry Buffers Inside the Frame Loop

**Learning:** Calling `gl.createBuffer()` and `gl.bufferData()` within every frame render pass (e.g. inside `blit()`, which runs ~15+ times per frame for fluid simulation passes) causes massive garbage collection pressure and driver overhead due to repeated buffer allocation and CPU-to-GPU data uploads.
**Action:** Always allocate static vertex and element array buffers once during WebGL initialization and simply bind them during render calls (`blit`).
