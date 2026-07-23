# Bolt's Journal - Critical Learnings Only

## 2024-07-23 - WebGL Buffer Allocation Bottleneck
**Learning:** In the vanilla WebGL fluid simulation, the `blit` function was creating and uploading data to new vertex and element array buffers on every frame inside the rendering loop (`requestAnimationFrame`). This causes significant garbage collection overhead, memory fragmentation, and GPU driver overhead by constantly re-allocating memory on the GPU. Reusing a single static WebGLBuffer for vertex data and index data resolves this, lowering CPU/GPU frame times and preventing GC-induced stutter.
**Action:** Always allocate static WebGL resources once during initialization rather than on-demand in high-frequency rendering loops.
