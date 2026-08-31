## 2025-08-31 - WebGL Buffer Allocation Churn in Animation Loops

**Learning:** Re-creating WebGL buffers (`gl.createBuffer()`) and re-uploading quad geometry (`gl.bufferData()`) inside a `blit` function called multiple times per frame (e.g. 15+ times/frame in a fluid simulation) causes severe GPU memory churn, GC pauses, and CPU driver overhead.
**Action:** Always allocate static WebGL geometry buffers once during application setup and bind the existing buffer references during render passes.
