# Bolt's Journal - Critical Learnings Only

## 2024-07-31 - WebGL Buffer Recreation inside Render Loop
**Learning:** In WebGL, allocating GPU buffers (`gl.createBuffer`) and uploading static data (`gl.bufferData`) inside rendering functions called multiple times per frame (e.g. `blit`) is a massive performance anti-pattern. It creates heavy CPU-to-GPU data transfer overhead, forces the GPU driver to constantly re-allocate memory, and produces a large volume of temporary JS objects, causing GC stuttering.
**Action:** Always extract static geometry buffer creation into a one-time setup phase at initialization, and only bind and reuse those buffers inside the frame rendering loop.
