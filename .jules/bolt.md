# Bolt's Journal ⚡

## 2024-07-22 - Static WebGL Buffer Creation Bottleneck
**Learning:** In the vanilla WebGL fluid simulation, the hot `blit` function is invoked around 16 times per frame (e.g. for every Jacobi pressure iteration and advection step). Creating new vertex and index buffers (`gl.createBuffer`) and re-uploading duplicate static vertex coordinates via `gl.bufferData` inside this hot path causes severe CPU-to-GPU bandwidth saturation, driver overhead, and garbage collection pauses due to frequent creation of typed arrays.
**Action:** Move buffer initialization out of the render loop. Pre-allocate and initialize static WebGL buffers once during application startup, and reuse those bindings in the hot path.
