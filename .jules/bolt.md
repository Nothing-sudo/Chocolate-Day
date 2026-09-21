## 2025-02-16 - Pre-allocate static WebGL geometry buffers
**Learning:** Calling `gl.createBuffer()` and `gl.bufferData()` inside frame-loop draw helper functions (like `blit()`) causes thousands of WebGL object allocations and TypedArray garbage collection allocations per second (60 FPS * ~17 blits = 1,020 allocations/sec).
**Action:** Always pre-allocate static quad vertex/element buffers during WebGL initialization and bind/reuse them inside render loop functions.
