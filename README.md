# IOL-AI 2026 — testing a submission on Colab

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/rita-berrada/iolai-2026-workshop/blob/main/linguini_eval_T4.ipynb)

A Colab notebook that runs an IOL-AI 2026 submission — [`script.py`](https://huggingface.co/ritaberrada/iol-qwen25-14b-awq/blob/main/script.py) from `ritaberrada/iol-qwen25-14b-awq` — on [Linguini](https://huggingface.co/datasets/facebook/linguini) problems, so you can **see what the script does and check its answers before uploading to Hugging Face**.

The prompt, model, and parsing are exactly what gets submitted. Only three things change for Colab:

1. **Install the AWQ loader** — Colab has internet; the offline sandbox has it preinstalled.
2. **Use Linguini** (it ships reference answers) instead of the hidden test set.
3. **Compare answers directly** instead of writing `submission.csv`.

## Run it

1. Open [`linguini_eval_T4.ipynb`](linguini_eval_T4.ipynb) in Colab (badge above).
2. **Runtime → Change runtime type → T4 GPU**.
3. **Runtime → Run all** (~15 min; downloads ~10 GB of model weights).

## What each cell does

| Cell | Does |
|---|---|
| Setup | Install dependencies (Colab-only) |
| 1. Load the model | Qwen2.5-14B-Instruct-AWQ from the Hub |
| 2. Prompt & parser | **Identical to the submission** |
| 3. Test data | Linguini instead of the hidden test set |
| 4. Run the script | The submission's generation loop |
| 5. See the output | Raw generation + parsed answers per problem |
| 6. Check answers | Exact-match + chrF vs the references |

**Data note:** please do not re-host Linguini problems in plaintext (contamination risk) — the notebook loads them from the Hub only.
