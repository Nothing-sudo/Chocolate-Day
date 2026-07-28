## 2024-11-04 - WebGL Buffer Allocation Leak in Hot Render Loops
**Learning:** In highly active rendering loops, calling `gl.createBuffer()` and `gl.bufferData()` within the render/blit function creates and leaks WebGL buffers constantly. Since WebGL garbage collection for native buffers is highly delayed and expensive, this causes huge memory/GC pressure and GPU overhead.
**Action:** Always allocate static vertex and index buffers once during initialization (e.g., `initBuffers()`), and only bind the existing buffers inside the render/blit loop.
