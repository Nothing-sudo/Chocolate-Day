## 2026-08-25 - Avoid per-frame WebGL buffer allocation in blit loops
**Learning:** Calling `gl.createBuffer()` and instantiating TypedArrays inside `blit()` calls (executed 15+ times per frame) allocates ~900 buffers/arrays per second at 60 FPS, causing severe GC pauses and WebGL API overhead.
**Action:** Pre-allocate static full-screen quad vertex and index buffers once during WebGL initialization and bind them during `blit()` execution.
