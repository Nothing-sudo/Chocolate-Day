# Bolt's Journal - Critical Learnings Only

## 2025-08-07 - WebGL Static Geometry Buffer Allocations in Render Loop
**Learning:** Instantiating WebGL geometry buffers (`gl.createBuffer()`) and re-uploading vertex/index data (`gl.bufferData()`) dynamically inside a render/blit loop that executes multiple times per frame is highly inefficient. It results in major GPU/CPU synchronization stalls, driver overhead, and severe memory thrashing (garbage collection pressure).
**Action:** Always pre-allocate static geometry buffers once during WebGL initialization and bind/reuse them inside render/blit functions. This completely eliminates dynamic per-frame GPU buffer creation and data uploads.
