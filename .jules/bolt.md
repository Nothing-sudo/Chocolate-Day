# Bolt's Journal - Critical Learnings Only

## 2024-02-14 - WebGL Buffer Allocation Bottleneck
**Learning:** In the `blit` function, WebGL static geometry buffers (`createBuffer`, `bufferData`) were being reallocated and re-uploaded on every single frame and shader pass. Since `blit` is called dozens of times per frame (due to pressure solver iterations, advection, etc.), this represents a major overhead, causing driver overhead, CPU-GPU sync stalls, and garbage collection churn.
**Action:** Create the vertex buffer and index buffer once during initialization, bind and reuse them in `blit()`, eliminating per-frame allocations and data transfers.
