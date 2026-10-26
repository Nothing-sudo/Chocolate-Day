## 2024-10-26 - Pre-allocate Static WebGL Quad Buffers
**Learning:** Re-creating WebGL vertex and element index buffers inside per-frame drawing functions (like `blit`) causes massive GPU memory allocations, JS heap churn, and GC pauses (30+ buffer creations/sec per draw call).
**Action:** Always create and initialize static geometry buffers once during WebGL initialization and re-bind them inside frame render calls.
