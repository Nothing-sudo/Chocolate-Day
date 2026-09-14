## 2026-09-14 - Reuse WebGL Static Buffers across Blit Calls
**Learning:** Re-allocating and re-uploading static WebGL quad geometry buffers inside rendering loop passes (`blit()`) generates significant allocation churn (~1,000+ buffer allocations per second) and CPU-to-GPU bus transfers. Pre-creating buffers during WebGL context initialization and binding existing handle references in `blit()` avoids garbage collection pressure and driver overhead.
**Action:** Always allocate static WebGL geometry buffers once during setup and bind pre-allocated buffers inside animation loop render passes.
