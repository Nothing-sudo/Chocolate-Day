## 2024-07-24 - Avoid runtime WebGL buffer re-allocations
**Learning:** Instantiating WebGL buffers (via `gl.createBuffer()` and `gl.bufferData()`) on every frame/pass in the hot render loop creates significant GC (garbage collection) pressure and introduces synchronous CPU-to-GPU memory copy bottlenecks. Pre-allocating and re-using static buffers once at setup eliminates these performance issues.
**Action:** Always inspect the WebGL draw/blit calls to ensure that index, vertex, and other static buffers are allocated during setup/init phases rather than inside hot paths.
