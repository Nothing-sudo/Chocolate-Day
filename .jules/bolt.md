## 2026-10-05 - WebGL Static Quad Buffer Allocation inside Frame Loop
**Learning:** Calling `gl.createBuffer()` and `new Float32Array(...)` inside helper functions like `blit()` that execute multiple times per frame (~15 calls/frame) creates excessive Garbage Collection pressure (~1,000 typed arrays/sec) and causes WebGL driver GPU buffer allocation overhead.
**Action:** Allocate and populate static WebGL buffers (e.g., full-screen quads) once during program initialization and reuse the buffer handles in draw calls.
