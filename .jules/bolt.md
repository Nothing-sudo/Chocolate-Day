# Bolt's Journal - Critical Learnings

## 2025-11-07 - WebGL Static Geometry Buffer Re-allocation in Simulation Loop
**Learning:** In WebGL render loops (specifically shader simulation pipelines like fluid dynamics where `blit()` is called 15+ times per frame across multiple program passes), allocating buffers with `gl.createBuffer()` and re-uploading quad geometry via `gl.bufferData()` within the draw loop causes severe CPU overhead, GPU driver thrashing, and high JS heap GC pressure (~1000 allocations/sec at 60fps).
**Action:** Always pre-allocate static full-screen quad vertex and index buffers once during context/program initialization before the render loop starts (or before `initFBOs()`), and simply bind them in `blit()`.
