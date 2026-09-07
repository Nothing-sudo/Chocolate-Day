## 2025-02-14 - WebGL Buffer Allocation Overhead in Hot Rendering Loop
**Learning:** Calling `gl.createBuffer()` and `gl.bufferData()` inside a per-frame or per-pass render helper (like `blit()`) creates thousands of GPU buffer objects and typed array allocations per second, leading to high garbage collection pause frequencies and GPU driver resource allocation churn.
**Action:** Always pre-allocate static geometry vertex and index buffers once during WebGL initialization and rebind them during draw calls.
