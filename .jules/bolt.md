## 2026-08-22 - Reusing WebGL Static Quad Buffers in Blit Pass
**Learning:** Re-creating WebGL array and element buffers inside `blit()` on every frame (called ~14+ times per frame) allocates thousands of WebGL objects per second, causing severe Garbage Collection pauses and high CPU-to-GPU data transfer overhead.
**Action:** Allocate full-screen quad vertex and index buffers once during WebGL initialization and bind/reuse them across render passes in `blit()`.
