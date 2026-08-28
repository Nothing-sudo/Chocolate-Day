## 2026-08-28 - Avoid Per-Frame WebGL Buffer Creation in Blit Pass
**Learning:** Calling `gl.createBuffer()` and `gl.bufferData()` repeatedly inside `blit()` during each frame (~15+ invocations per frame) creates massive WebGL driver allocation overhead and garbage collection pressure on the main thread.
**Action:** Create and upload full-screen quad vertex and index buffers once during WebGL context initialization and bind/reuse them inside `blit()`.
