# Bolt's Journal - Critical Learnings

## 2025-02-14 - Static WebGL Buffer Allocation
**Learning:** Re-creating WebGL array buffers and uploading quad geometry inside `blit()` on every draw call (~16 times per frame, 60fps) creates significant GC pressure and unnecessary driver overhead.
**Action:** Allocate and bind static vertex/index buffers once during initialization and reuse them across all blit operations.
