# Bolt's Journal ⚡

## 2026-03-06 - WebGL Buffer Recreation Anti-pattern in Render Loop
**Learning:** In WebGL, creating buffers (`gl.createBuffer`) and uploading static geometry data (`gl.bufferData`) inside functions called within the rendering loop (such as `blit()`) is a severe performance bottleneck. It causes continuous memory allocation, triggers frequent garbage collection (GC) overhead, and introduces substantial driver-level CPU/GPU serialization delays.
**Action:** Always instantiate static geometry vertex and index buffers once during initialization. Bind and reuse these pre-allocated buffers inside the rendering loop instead of recreating them on every frame.
