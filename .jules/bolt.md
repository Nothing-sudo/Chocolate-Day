## 2026-10-09 - WebGL Quad Buffer Allocation in Fluid Simulation Loop

**Learning:** Re-creating `ARRAY_BUFFER` and `ELEMENT_ARRAY_BUFFER` via `gl.createBuffer()` and `gl.bufferData()` inside helper functions like `blit()` on every frame (15+ times per frame during pressure/divergence/advection passes) causes 900+ WebGL buffer allocations per second, leading to GC pauses and WebGL driver overhead.

**Action:** Always create static WebGL quad vertex and index buffers once during setup and bind attribute pointers upfront when geometry does not change between draw calls.
