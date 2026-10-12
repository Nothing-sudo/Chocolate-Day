## 2025-02-12 - Reuse WebGL static quad buffers across frame draw calls
**Learning:** Calling `gl.createBuffer()` and instantiating `Float32Array`/`Uint16Array` inside WebGL helper routines like `blit()` (which run ~17 times per frame at 60 FPS) creates over 1,000 GPU buffer allocations and JS objects per second, leading to major GC stutter and GPU driver overhead.
**Action:** Always initialize static screen-quad vertex and element buffers globally during WebGL context setup and bind them inside draw calls without re-allocation.
