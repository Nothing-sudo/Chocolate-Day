## 2026-09-19 - Pre-allocate static WebGL quad buffers
**Learning:** Re-creating WebGL buffers and TypedArrays inside a multi-pass render loop (`blit()`) causes thousands of allocations per second, triggering heavy garbage collection pauses and unnecessary GPU buffer initialization.
**Action:** Always pre-allocate static geometry buffers (like full-screen quad vertex and index buffers) during WebGL initialization and rebind them in render passes.
