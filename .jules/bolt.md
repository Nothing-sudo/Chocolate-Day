## 2026-10-17 - Avoid Per-Frame WebGL Buffer Allocation in Quad Blit Passes
**Learning:** Re-creating WebGL buffers (`gl.createBuffer()`) and allocating JavaScript typed arrays (`new Float32Array`, `new Uint16Array`) inside render loop utility functions like `blit()` creates massive allocation overhead (~1,000 WebGL objects/sec at 60 FPS across ~15-17 passes per frame) and causes GPU memory pressure and GC pauses.
**Action:** Always allocate static WebGL buffers (vertex and index) once during initialization and re-bind them inside rendering loop passes.
