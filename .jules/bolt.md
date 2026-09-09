## 2025-02-14 - WebGL Buffer Allocation Bottleneck in Render Loop
**Learning:** Calling `gl.createBuffer()` and `gl.bufferData()` on every `blit()` execution in a WebGL animation loop (17+ times per frame at 60 FPS) causes severe GPU buffer allocation overhead and triggers constant JavaScript GC pauses.
**Action:** Always pre-allocate static geometry vertex and element index buffers during WebGL context initialization and bind/reuse them inside render functions.
