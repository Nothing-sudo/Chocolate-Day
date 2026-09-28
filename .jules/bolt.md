## 2024-09-28 - Reusing static WebGL quad buffers in render loop
**Learning:** In WebGL applications, calling `gl.createBuffer()` and `gl.bufferData()` with new Float32Array/Uint16Array instances inside frequent frame blits (`blit()`) creates thousands of GPU buffer objects per second and causes severe JavaScript garbage collection stuttering.
**Action:** Always allocate static WebGL geometry buffers once during application setup and bind/reuse them across render passes.
