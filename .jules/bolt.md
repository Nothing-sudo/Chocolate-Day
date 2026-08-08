# Bolt's Journal - Critical Learnings

## 2026-03-06 - Initial Profile
**Learning:** Found that the `blit()` function in `script.js` creates WebGL buffers (vertex and index buffers) on *every single invocation* inside the render loop. This causes massive memory reallocation and driver overhead per frame.
**Action:** Create static WebGL buffers once during initialization, reuse them in `blit()`, and avoid dynamic allocation inside the rendering loop.
