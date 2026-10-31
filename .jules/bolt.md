## 2025-02-14 - Pre-allocate static WebGL geometry buffers outside render loop
**Learning:** Re-creating WebGL vertex and element array buffers (`gl.createBuffer()`) and allocating typed arrays on every blit invocation in a fluid simulation loop generates massive memory churn (~1,800 buffer allocations/sec at 60 FPS across 15+ blits/frame) and triggers WebGL driver state synchronization penalties and GC pauses.
**Action:** Always allocate static fullscreen geometry buffers once at initialization and reuse them across all draw/blit calls.
