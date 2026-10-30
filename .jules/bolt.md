## 2026-10-30 - WebGL Static Geometry Buffer Reuse

**Learning:** Re-creating WebGL buffers (`gl.createBuffer()`) and instantiating TypedArrays (`Float32Array`, `Uint16Array`) inside the frame render loop (such as inside `blit()`) creates thousands of GPU object allocations and garbage collection pressure every second. Pre-allocating and uploading static geometry buffers during setup and binding them in the render loop drastically reduces memory allocations and GPU driver overhead.

**Action:** When working with WebGL render loops, always ensure quad/vertex buffers for full-screen passes or static geometry are initialized once at startup and reused across frame draws.
