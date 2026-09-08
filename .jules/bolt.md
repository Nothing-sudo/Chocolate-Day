## 2025-05-18 - WebGL Buffer Allocation Overhead in Frame Loop

**Learning:** Re-allocating WebGL buffers (`gl.createBuffer()`) and buffering static quad vertex/index data (`gl.bufferData()`) inside a rendering function (`blit()`) called 10-20+ times per frame generates substantial WebGL driver overhead and JS garbage collection pressure.

**Action:** Pre-allocate static geometry buffers (such as full-screen quad vertex and index buffers) once during context setup and bind/reuse them across render passes inside the animation loop.
