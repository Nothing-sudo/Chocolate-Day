## 2025-02-20 - Reusing static WebGL quad buffers in animation loops
**Learning:** Calling `gl.createBuffer()` and `gl.bufferData()` within rendering helper functions like `blit()` creates and uploads new GPU buffers ~16 times per frame (~960 buffer allocations and uploads per second at 60 FPS), causing unnecessary GPU memory turnover, CPU driver overhead, and garbage collection pressure.
**Action:** Allocate vertex and index buffers once during WebGL initialization before any draw calls (including initial FBO setup) and bind the cached buffer references during draw calls.
