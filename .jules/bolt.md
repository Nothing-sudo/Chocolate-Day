## 2024-08-16 - WebGL Quad Buffer Pre-allocation
**Learning:** Recreating static vertex and element array WebGL buffers inside frequent render functions (`blit`) causes high allocation churn and garbage collection pauses (~15 buffer allocations per frame at 60 FPS).
**Action:** Pre-allocate static geometry buffers (`ARRAY_BUFFER` and `ELEMENT_ARRAY_BUFFER`) once during WebGL initialization and bind/reuse them inside render passes.
