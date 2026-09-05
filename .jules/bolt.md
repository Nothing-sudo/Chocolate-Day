## 2025-02-14 - WebGL Buffer Allocation in Frame Render Loop
**Learning:** In WebGL render loops, allocating GL buffers (`gl.createBuffer()`) and buffering static geometry data (`gl.bufferData()`) on every pass or draw call creates severe CPU/GPU driver overhead and JS garbage collection pressure.
**Action:** Always allocate static quad vertex/index buffers once during initialization and reuse them in render target draw calls (`blit()`).
