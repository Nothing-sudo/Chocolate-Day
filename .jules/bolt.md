## 2026-08-15 - Reuse Static WebGL Buffers across Render Passes

**Learning:** Re-creating WebGL buffers (`gl.createBuffer()`, `gl.bufferData()`) and typed arrays on every `blit()` render pass inside a 60FPS render loop creates massive garbage collection pressure (~1800 allocations/sec) and unnecessary WebGL driver allocation overhead.
**Action:** Pre-allocate static full-screen quad vertex and index buffers once during WebGL initialization and bind/reuse them across all render passes.
