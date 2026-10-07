## 2026-10-07 - WebGL Quad Buffer Allocation in Render Loop
**Learning:** Calling `gl.createBuffer()` and instantiating `Float32Array`/`Uint16Array` inside a WebGL `blit()` function invoked ~15+ times per frame causes severe garbage collection pressure and unnecessary WebGL buffer uploads.
**Action:** Always allocate static WebGL geometry and index buffers once during setup/initialization and bind the cached buffers inside `blit()`.
