## 2026-11-10 - WebGL Buffer Allocation Inside Render Loops
**Learning:** In WebGL render loops, allocating vertex and index buffers (`gl.createBuffer()` and `gl.bufferData()`) per `blit()` draw call creates thousands of short-lived GPU buffer objects and garbage collection pressure without being freed.
**Action:** Allocate static geometry buffers once at initialization and reuse them by binding in the draw loop, ensuring buffers are instantiated before any initialization function (like `initFBOs()`) invokes `blit()`.
