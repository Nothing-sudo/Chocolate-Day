## 2025-02-10 - Pre-allocate Static WebGL Geometry Buffers
**Learning:** Calling `gl.createBuffer()` and instantiating `Float32Array`/`Uint16Array` objects inside per-frame render routines (`blit`) creates massive garbage collection churn (~900 allocations/sec at 60 FPS across ~15 passes) and state setup overhead.
**Action:** Always instantiate static geometry buffers (e.g. quad vertices and indices) once during initialization and rebind them inside frame drawing routines.
