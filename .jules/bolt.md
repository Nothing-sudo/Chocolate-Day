## 2026-10-06 - Pre-allocate static WebGL geometry buffers
**Learning:** Instantiating WebGL buffers (`gl.createBuffer()`) and TypedArrays (`Float32Array`, `Uint16Array`) inside per-frame render routines like `blit()` causes severe garbage collection pauses and frame drops due to thousands of allocations per second.
**Action:** Always allocate static WebGL geometry buffers once during WebGL initialization and bind/reuse them across render passes.
