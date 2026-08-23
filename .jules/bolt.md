## 2024-02-14 - Pre-allocate WebGL Quad Buffers for Blit Passes

**Learning:** Creating GPU buffers with `gl.createBuffer()` and re-uploading quad vertex/index data with `gl.bufferData()` on every `blit()` execution in a render loop (~15+ times per frame at 60 FPS) introduces heavy GPU driver overhead and garbage collection pressure.

**Action:** Always pre-allocate static geometry buffers (such as full-screen quads) once during initialization and bind existing buffers during draw passes.
