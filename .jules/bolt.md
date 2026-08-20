# Bolt's Journal - Critical Learnings

## 2024-08-20 - WebGL Static Geometry Buffer Reuse
**Learning:** Re-creating WebGL array and element buffers inside render loop utility functions (`blit`) creates massive CPU/GPU object allocation and GC pressure, especially when invoked multiple times per frame (e.g. multi-pass fluid simulations with pressure iterations). Pre-allocating quad geometry buffers during WebGL initialization eliminated thousands of buffer creations per second.
**Action:** Always extract static geometry buffer allocations outside of per-frame render routines in WebGL applications.
