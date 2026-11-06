## 2025-02-03 - WebGL Full-Screen Quad Buffer Allocation in Render Loop

**Learning:** `blit()` was creating fresh WebGL array and element array buffers and uploading quad geometry to the GPU on every single draw call (~16-18 calls per frame at 60fps = ~1000 buffer allocations/sec). Because `initFBOs()` internally triggers `blit()` during startup, any statically cached quad buffers must be instantiated before `initFBOs()` runs.
**Action:** Statically allocate vertex and index buffers once during WebGL context initialization and bind them during `blit()` instead of calling `createBuffer()` and `bufferData()` on every draw.
