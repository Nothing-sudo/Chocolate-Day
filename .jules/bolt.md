## 2025-05-10 - WebGL Buffer Allocation in Draw Loops
**Learning:** Instantiating `gl.createBuffer()` and re-uploading static geometry arrays (`Float32Array`, `Uint16Array`) inside frame-rate `blit()` calls creates massive garbage collection pressure (~1000+ allocations/sec at 60 FPS) and memory leak issues.
**Action:** Always allocate static WebGL geometry buffers once during context setup (`initBuffers()`) and bind/reuse them across render passes.
