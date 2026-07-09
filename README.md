# IOL-AI 2026 — test your script on Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/rita-berrada/iolai-2026-workshop/blob/main/linguini_eval_T4.ipynb)

A template to **test your IOL-AI 2026 competition script on Colab before submitting it**. It runs your model on real [Linguini](https://huggingface.co/datasets/facebook/linguini) problems (same format as the competition test set), so you can see what your script produces and check its answers.

## How it's organised

- **Setup** + **Load the test problems** — Colab scaffolding, you don't touch it.
- **Your script** — your model + prompt + parsing. The part you experiment with and upload as `script.py`.
- **Check** — look at the raw output and score it (only possible here, where the answers are known).

## Reuse it for your own script

Change three things, all in the **Your script** section:

1. `MODEL_ID` → your model repo (or any model that fits the T4's 16 GB).
2. `SYSTEM` → your prompt (the main lever).
3. `parse_answers` → how you read the answers back (must match the format your prompt asks for).

Then run, watch the output stream live, and check the score — iterate on the prompt until you're happy.

## From this notebook to a real submission

Only three more things change:

1. `MODEL_ID` points at `.` (weights ship inside the submission repo) instead of a Hub name.
2. You read the platform's hidden test set at `/tmp/data/test.csv` instead of Linguini.
3. You write `submission.csv` instead of scoring.

The prompt, the model, and the parsing stay exactly the same.

## Run it

1. Open [`linguini_eval_T4.ipynb`](linguini_eval_T4.ipynb) in Colab (badge above).
2. **Runtime → Change runtime type → T4 GPU**.
3. Run the cells in order. Setup restarts the runtime once (normal) — after it restarts, continue from "Load the test problems". ~15 min total; downloads ~10 GB of model weights.

**Data note:** please do not re-host Linguini problems in plaintext (contamination risk) — the notebook loads them from the Hub only.
