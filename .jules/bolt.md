## 2025-02-14 - WebGL Buffer Allocation in Rendering Loop
**Learning:** Re-creating WebGL buffers (`gl.createBuffer()`) and uploading data (`gl.bufferData()`) inside functions called multiple times per frame (e.g. `blit()` invoked 15+ times per frame) causes massive GC pressure and CPU/GPU memory allocation overhead.
**Action:** Always allocate static WebGL buffers once during setup and bind them in render/blit routines.
