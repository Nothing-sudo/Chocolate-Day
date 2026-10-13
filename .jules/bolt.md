## 2026-10-13 - Avoid Per-Frame WebGL Buffer Allocation
**Learning:** Calling `gl.createBuffer()` and `gl.bufferData()` with newly instantiated `Float32Array`/`Uint16Array` objects inside per-frame drawing functions (like `blit()`) creates excessive GPU object creation overhead and JS Garbage Collection (GC) pressure in animation loops (~15+ buffer creations per frame).
**Action:** Pre-allocate static full-screen quad vertex and index buffers once during WebGL context initialization and reuse them across all rendering passes in `blit()`.
