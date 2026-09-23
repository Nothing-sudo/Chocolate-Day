# Bolt's Journal - Critical Learnings

## 2024-05-20 - Static Quad Buffer Allocation in WebGL Loop
**Learning:** Re-creating WebGL buffers (`gl.createBuffer()`) and re-uploading attribute/element data (`gl.bufferData()`) inside a frequently called render helper (`blit()`) causes thousands of allocations per second, leading to high GC pressure and GPU pipeline stalls.
**Action:** Always allocate static geometry buffers (like full-screen quad vertex and index buffers) once during initialization and reuse them inside render loops.
