## 2026-09-11 - Reuse WebGL Quad Buffers in Frame Loop
**Learning:** Calling `gl.createBuffer()` and uploading vertex/index data via `gl.bufferData()` on every `blit()` execution (15+ times per frame inside `requestAnimationFrame`) allocates over 1,000 GPU buffers per second, causing massive WebGL driver overhead and Garbage Collection pauses.
**Action:** Always pre-allocate static geometry buffers (such as full-screen rendering quad vertex and element buffers) during WebGL initialization and re-bind existing buffer handles inside render loops.
