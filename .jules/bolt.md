## 2025-02-17 - Static WebGL Buffer Reuse in Render Loops
**Learning:** Allocating WebGL vertex and element array buffers (`gl.createBuffer()`) and re-uploading buffer data (`gl.bufferData()`) on every frame/draw pass causes high CPU allocation overhead and triggers frequent garbage collection pauses, degradation of FPS in WebGL fluid simulations.
**Action:** Always pre-allocate static geometry buffers (such as full-screen quads used in post-processing/fluid simulation blit operations) once during WebGL context initialization and bind the existing buffers during render passes.
