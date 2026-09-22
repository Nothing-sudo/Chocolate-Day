## 2025-05-18 - Avoid per-frame WebGL buffer allocation in render loops
**Learning:** Re-creating WebGL buffers (`gl.createBuffer()`) and allocating typed arrays inside utility functions like `blit()` on every frame (~16+ times per frame) causes significant garbage collection pressure and WebGL API overhead.
**Action:** Always allocate static geometry buffers (e.g. full-screen quad vertex/index buffers) once during initial WebGL context setup and reuse them across render calls.
