# Bolt's Journal - Critical Learnings

## 2025-02-23 - Static WebGL Buffer Pre-allocation
**Learning:** Re-creating WebGL buffers (`gl.createBuffer()`, `gl.bufferData()`) inside rendering utility functions (like `blit()`) called multiple times per frame creates severe garbage collection pressure (~960 buffer allocations/sec) and GPU driver allocation overhead.
**Action:** Pre-allocate static quad vertex and element buffers once during WebGL initialization and bind/reuse them inside the `blit` function.
