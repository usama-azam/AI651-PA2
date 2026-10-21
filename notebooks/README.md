# Notebooks

These are the Kaggle notebooks with their outputs. All were run on a Tesla T4, PyTorch 2.11.

| File | What it does | Produces |
|---|---|---|
| `PA2_Q2_Step1_data_and_Table1.ipynb` | data, split, `mirror` / `rotate` / `make_window`, checks | Table 1 |
| `PA2_Q2_Step2_Figure1_optical_flow.ipynb` | Farneback optical flow on 50 training videos | Figure 1 (950 pairs, 103,050 pixels, median 3.32 px/frame) |
| `PA2_Q2_Step3_build_model_A.ipynb` | ConvLSTM cell, model A, automatic checks | parameter count 480,784 |
| `PA2_Q2_Step4_train_A.ipynb` | training run for model A (seeds 0, 1) | `checkpoints/A_seed*.pt`, `logs/A_seed*.json` |
| `PA2_Q2_Step4_train_B_C.ipynb` | the same notebook, run for models B and C | B and C checkpoints and logs |
| `PA2_Q2_Step4_train_D.ipynb` | the same notebook with `ModelD` (dilated layer 2), run for model D | D checkpoints and logs |
| `PA2_Q2_Step5_test_model_A.ipynb` | evaluation of model A | Tables 2–4, Figures 2–5, Figure 3 GIFs |
| `PA2_Q2_Step6_models_ABCD_and_final.ipynb` | reach check, models A–D, symmetrised models | Tables 5–6, Figure 6, Figure 6 GIFs |
