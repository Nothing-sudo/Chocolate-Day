# Bolt's Performance Journal

## 2025-08-01 - WebGL Buffer Re-creation inside Render Loop
**Learning:** In static WebGL projects running inside rendering loops, creating new buffers (with `gl.createBuffer()` and uploading data via `gl.bufferData()`) on every single frame/blit call introduces significant memory allocations, garbage collection overhead, and CPU-to-GPU bandwidth bottlenecks.
**Action:** Move buffer creation and initialization to the startup phase, and reuse the single static vertex/index buffer object across all blit operations inside the rendering loop.
