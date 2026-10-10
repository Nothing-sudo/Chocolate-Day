## 2024-10-10 - Reuse static WebGL geometry buffers across animation frames
**Learning:** Recreating WebGL ARRAY_BUFFER and ELEMENT_ARRAY_BUFFER via `gl.createBuffer()` and instantiating TypedArrays inside `requestAnimationFrame` loop creates severe GC pressure and WebGL object churn (30+ allocations per frame in multi-pass shaders like fluid simulation).
**Action:** Always allocate static geometry buffers (e.g. full-screen quad vertices and indices) once during WebGL initialization and bind/reuse them inside render/blit functions.
