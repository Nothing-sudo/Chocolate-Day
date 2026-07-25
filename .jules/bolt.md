## 2026-07-25 - Caching WebGL Buffers in Dynamic Fluid Simulation
**Learning:** Instantiating new WebGL buffers and re-uploading quad positions/indices to the GPU on every `blit` call (~15-17 times per frame) creates severe CPU/GPU bottleneck and triggers aggressive garbage collection thrashing in high-frequency rendering loops.
**Action:** Always pre-create and cache static geometry buffers (such as full-screen quads used for blitting) and reuse them across draw calls, only binding and invoking `vertexAttribPointer` rather than recreating the buffers.
