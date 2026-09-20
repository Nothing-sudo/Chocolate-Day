## 2026-09-20 - Pre-allocate Static WebGL Quad Buffers in Rendering Pass
**Learning:** In WebGL applications, calling `gl.createBuffer()` and instantiating typed arrays (`Float32Array`, `Uint16Array`) inside per-frame pass routines like `blit()` causes severe memory allocation overhead and driver stall (~15-17 buffer creations per frame, >1000/sec).
**Action:** Pre-allocate static full-screen quad vertex and index buffers during WebGL initialization and bind/reuse them across render passes.
