## 2026-10-25 - Avoid per-frame WebGL buffer creation in blit routines
**Learning:** Re-creating `gl.createBuffer()` and re-uploading quad vertex/index data on every `blit()` call (~17x per frame in fluid simulations) causes severe Garbage Collection (GC) pressure and unnecessary GPU re-allocations.
**Action:** Always pre-allocate static geometry buffers (such as full-screen quads) during WebGL initialization and re-bind existing buffer handles inside render loops.
