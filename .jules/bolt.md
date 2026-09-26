## 2026-09-26 - Avoid WebGL Buffer Re-allocation in Rendering Loops
**Learning:** Re-allocating WebGL buffers (`gl.createBuffer()`) and uploading typed array vertex data (`gl.bufferData()`) inside per-frame `blit()` calls creates ~1,800 WebGL object allocations and typed array creations per second, causing severe GC pressure and frame stutter in animation loops.
**Action:** Pre-allocate static quad vertex and element buffers once during WebGL initialization and bind/reuse them inside render/blit functions.
