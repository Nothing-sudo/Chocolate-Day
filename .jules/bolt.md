## 2026-09-06 - WebGL Buffer Allocation Inside Render Loops

**Learning:** Calling `gl.createBuffer()` and `gl.bufferData()` with newly instantiated typed arrays inside rendering functions executed multiple times per frame creates severe GC pressure (~900+ allocations/sec at 60 FPS) and WebGL state upload overhead.
**Action:** Always hoist static WebGL quad geometry buffers and attribute layout configuration out of the `render()` and `blit()` calls to startup time.
