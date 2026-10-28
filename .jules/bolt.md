## 2025-02-14 - Pre-allocate static WebGL geometry buffers
**Learning:** In WebGL render loops, helper functions like `blit()` that execute multiple times per frame (e.g., ~15-17 times during fluid simulation Jacobi pressure iterations) should never instantiate `gl.createBuffer()` or typed arrays (`Float32Array`/`Uint16Array`). Doing so creates severe garbage collection pauses and GPU allocation overhead (over 1,000 allocations/sec at 60 FPS).
**Action:** Always create static quad vertex and index WebGL buffers once during context initialization and bind/reuse them inside render functions.
