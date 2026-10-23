## 2025-05-18 - Pre-allocated WebGL Geometry Buffers in Simulation Render Loop

**Learning:** Re-creating WebGL buffers (`gl.createBuffer()`) and binding typed arrays inside `blit()` calls invoked 15+ times per frame causes heavy GC allocation churn and WebGL driver overhead. Pre-allocating quad vertex/index buffers once at init eliminates ~1,000 array and buffer allocations per second.

**Action:** Always audit WebGL rendering loops for inline `gl.createBuffer()`, `gl.bufferData()`, or array allocations, and hoist static quad/geometry buffer creations to context setup time.
