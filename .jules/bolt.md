## 2026-09-03 - Reuse static WebGL buffers in blit pass
**Learning:** Re-creating WebGL buffers (`gl.createBuffer()`) and re-specifying array data (`gl.bufferData()`) inside a render loop (especially during multipass shaders like fluid pressure iterations run ~15-20 times per frame) creates massive GPU driver overhead and garbage collection pressure (~1,920 buffer allocations/sec at 60 FPS).
**Action:** Always pre-allocate static geometry buffers (such as full-screen quads) during initialization and reuse buffer references in render loops.
