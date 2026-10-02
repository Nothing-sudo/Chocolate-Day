## 2026-10-02 - WebGL static geometry buffer re-use

**Learning:** Allocating WebGL buffers (`gl.createBuffer()`) and copying vertex data (`gl.bufferData()`) inside a frame rendering loop (such as in `blit()`) creates thousands of unmanaged GPU buffer objects per second and triggers constant JavaScript garbage collection.

**Action:** Static geometry (like full-screen quad vertex and index buffers) should be created once during WebGL initialization and bound/reused across all rendering draw calls.
