## 2024-08-17 - WebGL Static Geometry Buffer Allocation in Render Loop
**Learning:** Instantiating `gl.createBuffer()` and uploading `gl.bufferData()` on every `blit()` execution in a WebGL frame loop allocates dozens of redundant WebGL buffers per frame (~15+ calls per frame at 60 FPS), causing severe GPU/CPU memory churn and garbage collection pauses.
**Action:** Always pre-allocate static geometry buffers (such as full-screen quad vertex and element buffers) during WebGL initialization and simply bind them in render/blit routines.
