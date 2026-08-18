## 2025-02-14 - Pre-allocate WebGL Quad Geometry Buffers
**Learning:** Re-creating WebGL buffers with `gl.createBuffer()` and `gl.bufferData()` inside animation loop helpers (like `blit()`) causes ~1000 buffer allocations/sec at 60 FPS, creating CPU overhead and GC churn.
**Action:** Always allocate static full-screen quad vertex and index buffers once during WebGL context setup and reuse them during rendering.
