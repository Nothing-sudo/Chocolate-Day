## 2025-02-08 - Reuse static WebGL buffers across rendering passes

**Learning:** WebGL full-screen quad rendering helper functions (like `blit()`) invoked repeatedly per frame (e.g. 10-20+ times per frame for fluid simulation Jacobi pressure iterations and advection passes) should never allocate buffers or upload buffer data on every execution.
Creating new `ARRAY_BUFFER` and `ELEMENT_ARRAY_BUFFER` WebGL buffer objects and uploading data on every `blit()` call creates massive CPU-GPU allocation overhead, GPU driver command queue saturation, and JavaScript Garbage Collection pressure.
Creating static vertex and index quad buffers once during initialization and binding them during `blit()` reduces allocations per frame to zero.

**Action:** Whenever optimizing WebGL/Canvas rendering loops, check if static geometry quad/attribute buffers are allocated dynamically inside helper functions called on every frame. Hoist buffer initialization outside the render loop.
