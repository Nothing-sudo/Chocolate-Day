# Bolt's Performance Journal ⚡

## 2026-08-05 - WebGL Buffer Allocation Anti-Pattern in Fluid Simulation Loop
**Learning:** In the custom WebGL fluid simulation, the helper function `blit(target)` was dynamically creating new vertex and index buffers using `gl.createBuffer()`, loading vertex arrays, and binding them *every single render pass* (which is called dozens of times per frame). This caused thousands of WebGL buffer objects to leak, putting extreme pressure on CPU-GPU data transfers and memory garbage collection.
**Action:** Create the static full-screen quad vertex and index buffers once during initialization, store their references, and bind/reuse them inside the rendering loop (`blit`) rather than re-creating them on every frame.
