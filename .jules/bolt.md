## 2026-10-14 - Pre-allocate Static WebGL Geometry Buffers
**Learning:** Re-creating WebGL buffers inside `blit()` every frame creates thousands of GPU buffer allocations and JS typed array allocations per second (~15-17 passes/frame * 60 FPS), causing severe GC spikes and GPU overhead.
**Action:** Always pre-allocate static geometry buffers (like full-screen quad vertex and element buffers) during initialization and bind them inside the render loop.
