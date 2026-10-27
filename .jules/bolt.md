## 2024-02-13 - Reuse WebGL Quad Buffers to Eliminate Garbage Collection Churn

**Learning:** In WebGL render loops, creating new VBOs (`gl.createBuffer()`) and instantiating TypedArrays (`Float32Array`/`Uint16Array`) inside per-frame drawing routines (such as `blit()`, called ~16 times per frame) causes massive GC pressure, frame stutters, and unnecessary WebGL driver overhead.
**Action:** Always pre-allocate static geometry buffers (e.g. quad vertices and indices) once during WebGL setup/initialization and bind/reuse them across draw calls.
