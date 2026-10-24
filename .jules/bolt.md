## 2026-10-24 - Pre-allocating Static WebGL Geometry Buffers
**Learning:** Re-creating WebGL buffers (`gl.createBuffer`) and TypedArrays inside a render loop (such as `blit()` executed ~15-17 times per frame) causes massive CPU overhead, memory allocations (~1,000 arrays/sec), and GC pauses. Pre-allocating quad geometry buffers during startup completely eliminates GC overhead and buffer recreation costs.
**Action:** Always initialize static quad/geometry VBOs once globally and bind existing buffer handles in rendering loop passes.
