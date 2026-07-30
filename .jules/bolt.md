# Bolt's Journal - Critical Learnings

## 2025-03-06 - Static Geometry Buffer Recreation Anti-pattern in WebGL Rendering Loop
**Learning:** Instantiating new WebGL buffers (via `gl.createBuffer()` and uploading data via `gl.bufferData()`) on every single frame/blit call in a rendering loop leads to massive CPU-to-GPU overhead, continuous memory allocation leaks, and garbage collection pauses. Static full-screen quads and other fixed geometries should always be allocated and populated once during initialization, then bound and drawn repeatedly.
**Action:** Always pre-allocate and populate static WebGL buffers during setup/initialization, and bind/reuse them during runtime instead of recreating them inside drawing routines.
