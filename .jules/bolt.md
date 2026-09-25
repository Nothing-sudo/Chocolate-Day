## 2025-02-14 - WebGL Buffer Allocation in Animation Loop

**Learning:** Re-creating WebGL buffers (`gl.createBuffer()` and `gl.bufferData()`) inside a full-screen quad helper function (`blit()`) called multiple times per frame (~15+ times per frame during pressure/advection steps) causes severe CPU-to-GPU data transfer overhead and excessive garbage collection churn.

**Action:** Always allocate static screen-quad vertex and index buffers once during WebGL initialization and bind/reuse them inside rendering helper functions.
