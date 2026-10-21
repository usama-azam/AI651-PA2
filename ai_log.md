# AI use log

**Tool:** Claude (Anthropic), through the Claude desktop app, 13–21 October 2026.
**Role:** tutor and assistant.

All training and evaluation runs were executed by me on Kaggle. The AI only tested notebooks on synthetic data and never ran my real experiments.

## Code (notebooks)

| Notebook / part | AI output | My work |
|---|---|---|
| Step 1 | Notebook scaffold (data loading, splits, Table 1 checker) with explanations | I wrote `mirror`, `rotate`, `make_window`, `apply_g_inverse`. Mistakes the AI pointed out: `k=1` instead of `k=a` in `rot90`, and the target mask. |
| Step 2 | Scaffold (Farneback call, histograms), explanation of optical flow | I wrote `keep_mask` and `direction_deg` |
| Step 3 | Scaffold with automatic checks; after my attempts, a completed reference version of the cells | I wrote `ConvLSTMCell.forward`, `ModelA.step` and `ModelA.forward`, with corrections |
| Step 4 | Training notebook (protocol, seeds, timing, logs, model table A–D) | I wrote `masked_mse` and ran all training |
| Step 5 | Evaluation notebook (Tables 2–4, Figures 2–5, GIFs) | I wrote the two `per_video_CE` lines (C_T and E_T) and ran it |
| Step 6 | Evaluation notebook (reach check, Tables 5–6, Figure 6) | I wrote the `symmetrise` line; the AI corrected the function name `g_inv` → `apply_g_inverse` |
| Model D | Explanation of the ways to increase reach; candidate designs with parameter counts and measured reach; the 3-line `ModelD` class after my choice | I computed D1's reach (12 px) and why 5×5 kernels exceed the budget, and chose design D2 |

## Written answers

| Question | How it was produced |
|---|---|
| Q2.1 | I drafted all three parts. Claude corrected two errors: I compared bars to the median instead of the uniform line, and I said the model had "seen the transformations" rather than the directions. Claude polished the wording. |
| Q2.2 | I identified which factor each transformation changes. Claude added the mirror-vs-rotation comparison and the "held fixed" points, and polished the wording. |
| Q2.3 | I counted the convolutions on each path through guided questions. Claude corrected the tie between paths (a) and (b), added the diagonal working, and wrote the final wording. |
| Q2.4 | Guided checks (factor vs Blank, double penalty, blur, overlap). Claude wrote the final wording from my answers. |
| Q2.5 | Predictions and reasons chosen by me, before the experiments, from options drawn from my own Q2.1–Q2.3 results. Claude only turned my choices into sentences. Reproduced unedited. |
| Q2.6 | I answered the Blank-consistency check. Claude wrote the final wording and added the inequality C_T ≤ 2(E_T + E). |
| Q2.7 | I chose what each row shows for video 150 through guided checks. Claude wrote the description. |
| Q2.8 | I worked out the error ratios and chose "appearance" and the row-3 shape evidence. Claude wrote the final wording and computed the 13%/16% bin-change figures from my Figure 1 bins. |
| Q2.9 | I identified the breakdown speed, the stall + blur failure and the missed factors. Claude corrected my reach-agreement answer (6.64 < 8 px, so it does not agree) and wrote the final wording. |
| Q2.10 | I answered that model A alone cannot separate the causes, and that reach is the remaining cause. Claude corrected my choice of "bigger kernels" (an architecture change, not a training change) and wrote the final wording. |
| Q2.11 | Predictions chosen by me before training B–D (B → rotation, C → 2×, C and D → 3×). Claude only formatted them. Reproduced unedited. |
| Q2.12 | I chose design D2 and computed reach and parameters. Claude wrote the description and the measured reach check. |
| Q2.13 | I chose each label and the reason data cannot extend reach. Claude wrote the final wording and the caveats. |
| Q2.14 | I judged the 1× cost of each model. Claude argued for a conditional verdict on C (I had answered "No") and wrote the final wording. |
| Q2.15 | I identified the 8× inference cost and that averaging did not hurt. Claude corrected my answer on exactness (I had picked B) and wrote the proof and the final wording. |
| Q2.16 | Claude computed the per-video C_R and E_R for video 150 from my Step 6 results and wrote the answer. I checked it against my figures. |
| Q2.17 | I chose the verdict, the evidence and the untested case. Claude wrote it within 150 words and added why 4× needs longer videos. |
| Q1 | We went through the course's Q1 tutorial slides together. I made the main design decisions: a 6-hour history window, a directed graph with distances, and median + 10/90% quantile outputs. Claude wrote the full text of all six headings, the assumptions, the data table, the equations and the TikZ diagram, following the tutorial's skeleton. I reviewed it. |
| Report, README | Assembled and drafted by Claude from my result files and figures. I reviewed them. |
