# Bolt ⚡ Performance Optimization Journal

This journal documents critical codebase-specific performance learnings, bottlenecks, and insights gathered during performance optimization.

## 2026-07-27 - [WebGL Buffer Allocation Bottleneck in Fluid Simulation]
**Learning:** Re-creating dynamic WebGL buffers on every invocation of `blit` (which occurs dozens of times per frame in the fluid simulation render loop) creates severe garbage collection thrashing and unnecessary GPU memory re-allocations.
**Action:** Pre-allocate static Float32Array and Uint16Array vertex buffers once during startup. Modify `blit` to bind and reuse these pre-allocated buffers instead of re-instantiating them, eliminating hundreds of buffer allocations and garbage collections per second.
