## 2025-09-04 - WebGL Quad Buffer Pre-allocation
**Learning:** Re-creating WebGL buffers inside per-frame render routines like `blit()` causes memory allocation churn, GC pauses, and repeated GPU buffer re-upload overhead. Pre-allocating static quad vertex/element buffers once during initialization significantly decreases JS heap allocations and GPU driver overhead.
**Action:** When working with WebGL render loops, verify that static quad geometry buffers are created once and reused via `gl.bindBuffer()` instead of re-creating them on every frame.
