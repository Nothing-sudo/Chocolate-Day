## 2024-08-30 - WebGL Static Geometry Buffer Reuse
**Learning:** Re-creating WebGL buffers (`gl.createBuffer()`) and re-uploading quad vertex/index data (`gl.bufferData()`) inside a full-screen quad helper (`blit()`) executed 15+ times per frame causes severe garbage collection pressure and CPU-to-GPU memory transfer overhead.
**Action:** Always allocate static full-screen quad buffers once during WebGL context setup and reuse them across all rendering passes in the render loop.
