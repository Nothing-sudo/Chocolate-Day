## 2026-10-08 - WebGL Static Quad Buffer Re-use

**Learning:** Recreating WebGL ARRAY_BUFFER and ELEMENT_ARRAY_BUFFER inside every `blit()` call in the rendering loop allocates thousands of GPU buffers and typed arrays per second, causing massive memory thrashing and GC pauses.
**Action:** Always pre-allocate static geometry buffers once during WebGL initialization and bind/reuse them inside render/blit functions.
