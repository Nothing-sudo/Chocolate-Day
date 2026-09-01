# Bolt's Journal - Critical Learnings

## 2026-09-01 - WebGL Static Geometry Buffer Reuse
**Learning:** WebGL full-screen quad rendering in `blit()` was re-allocating `gl.createBuffer()` and re-uploading `Float32Array`/`Uint16Array` geometry data multiple times per frame (during advection, pressure, divergence, and display passes), creating high garbage collection pressure and driver allocation overhead.
**Action:** Allocate static geometry buffers once during WebGL initialization and bind/reuse them across render passes in `blit()`.
