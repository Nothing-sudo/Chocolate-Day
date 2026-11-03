# Bolt's Performance Journal - Critical Learnings

## 2025-02-03 - WebGL Buffer Allocation in Simulation Loop
**Learning:** Re-creating and re-uploading static WebGL geometry buffers (`gl.createBuffer()` and `gl.bufferData()`) inside a frequently called render/blit function (~16-17 calls per frame) creates massive memory churn, GPU-upload overhead, and GC pauses. Pre-allocating buffers at initialization time eliminates redundant driver work and improves frame timing consistency. Furthermore, initialization order matters: `initFBOs()` calls `blit()` during startup, so static quad buffers must be allocated prior to calling `initFBOs()`.
**Action:** When working with WebGL / Canvas rendering pipelines, always pre-allocate static geometry buffers and element arrays once before any framebuffer initialization or render loop execution.
