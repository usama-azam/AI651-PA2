# AI651 – Deep Learning for Space, Time and Graphs · Assignment 2

**Usama Azam** (25280109), LUMS, Fall 2026

- **Report (PDF):** [`report/DL4STG_PA2_report_Usama_Azam.pdf`](report/DL4STG_PA2_report_Usama_Azam.pdf), with LaTeX source in `report/latex/`
- **Question 1:** river forecasting proposal (design only, in the report)
- **Question 2:** *Motion or Memory?* — ConvLSTM forecasters on Moving MNIST, tested under mirror, rotation and faster playback

## Repository layout

| Folder | Contents |
|---|---|
| `notebooks/` | The six Kaggle notebooks (Step 1–6) that produce every table and figure |
| `checkpoints/` | Trained weights: models A, B, C, D, seeds 0 and 1 (`<model>_seed<seed>.pt`, PyTorch `state_dict`) |
| `logs/` | Training logs (loss per epoch, validation E(5), train time per epoch, inference time) |
| `results/` | Tables 2–6 as Markdown, the one-step reach check, per-video results (`.npz`), and the video numbers used in Figures 2, 3 and 5 |
| `figures/` | Figures 1–6 and supplementary figures as PNG |
| `gifs/` | Animated panels for Figure 3 and Figure 6(a) |

## Notebooks

| Notebook | What it does | Produces |
|---|---|---|
| Step 1 | Data loading, train/val/test split, mirror and rotation, window function, checks | Table 1 |
| Step 2 | Farneback optical flow on 50 training videos | Figure 1 |
| Step 3 | Model A (two-layer ConvLSTM, 480,784 parameters) with automatic checks | — |
| Step 4 | Training protocol (Adam 1e-3, batch 32, 30 epochs, seeds 0/1); one run for A, one for B and C, one for D | checkpoints, logs |
| Step 5 | Evaluation of model A: baselines, consistency tests, speed tests, GIFs | Tables 2–4, Figures 2–5 |
| Step 6 | Models A–D, measured reach, symmetrised models, final model | Tables 5–6, Figure 6 |

**How to reproduce:** run the notebooks in order on Kaggle (GPU T4, Internet on). For each notebook, add the previous notebook's output (or the files in `checkpoints/` and `logs/`) as input.

## Models

| Model | Architecture | Training speeds | Symmetry augmentation |
|---|---|---|---|
| A | 2-layer ConvLSTM, 3×3 kernels, patch 4 (reach 8 px) | 1× | none |
| B | as A | 1× | random element of the 8-element group |
| C | as A | k ∈ {1, 2, 3} | none |
| D | as A, but layer 2's conv dilated by 3 (reach 16 px, same 480,784 parameters) | k ∈ {1, 2, 3} | none |
| Final | D wrapped as a symmetrised forecaster (average over the 8 symmetries) | – | built in, exact |

## Main results

These are test-set means over seeds 0 and 1. Full tables are in `results/` and the report.

| Model | E(5) 1× | E_R | C_R | E(2) 2× | E(2) 3× |
|---|---|---|---|---|---|
| A | 0.0222 | 0.0240 | 0.00288 | 0.0442 | 0.0511 |
| B | 0.0229 | 0.0228 | 0.00134 | 0.0431 | 0.0490 |
| C | 0.0267 | 0.0279 | 0.00258 | 0.0288 | 0.0333 |
| D | 0.0285 | 0.0293 | 0.00171 | 0.0296 | 0.0332 |
| Symmetrised D (final) | 0.0284 | 0.0284 | 5e-17 | 0.0296 | 0.0331 |

## Hardware

All training and evaluation used Kaggle with an NVIDIA Tesla T4 and PyTorch 2.11.

## Use of AI

Generative AI (Claude, Anthropic) was used as a tutor and assistant, as allowed by the course policy. The details (prompts, outputs, edits) are in the report's appendix and in [`ai_log.md`](ai_log.md).
