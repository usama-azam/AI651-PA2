# AI use log — AI651 PA2 (tool: Claude)

| Date | What I asked (prompt) | What the AI gave (output) | What I did / changed myself |
|---|---|---|---|
| 14 Oct | "Explain me this assignment completely" | Overview of Q1 and Q2, work plan | Used as a reading guide |
| 14 Oct | Help to start Q2 | Step 1 notebook: data loading, skeletons, Table 1 checker | I wrote mirror, rotate, make_window, apply_g_inverse; AI pointed out my mistakes (k=1 in rotate, < vs <=) and I fixed them |
| 15 Oct | Figure 1 / optical flow | Step 2 notebook: flow loop, plotting, checks | I wrote keep_mask and direction_deg; interpreting Figure 1 is mine |
| 15–20 Oct | Build model A | Step 3 notebook: explanations, skeletons, checks; ConvLSTM study guide and diagrams | I filled the ConvLSTM cell, step and rollout; AI corrected errors (u vs x, outputs[4:]) |
| 20 Oct | Training | Step 4 notebook: data on GPU, window sampler, training loop, timing, logging | I wrote masked_mse; AI fixed a GPU rounding issue in its own check |
| — | (none) | — | Q2.3 reach and Q2.5 predictions written by me without AI |
