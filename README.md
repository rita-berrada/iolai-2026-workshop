# IOL-AI 2026 — Linguini submission preview

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/rita-berrada/iolai-2026-workshop/blob/main/linguini_eval_T4.ipynb)

A hands-on Colab notebook that previews **what a competition submission actually does** for [IOL-AI 2026](https://iolai.org). It runs a candidate model on real [Linguini](https://huggingface.co/datasets/facebook/linguini) linguistics-olympiad problems (the same format as the competition test set) and shows the **raw model output**, how it is parsed into answers, and how those answers are **scored** against the references.

Built as the walk-through for the workshop call.

## Run it

1. Open [`linguini_eval_T4.ipynb`](linguini_eval_T4.ipynb) in Google Colab (use the badge above).
2. **Runtime → Change runtime type → T4 GPU**.
3. **Runtime → Run all** (~15 min: ~3 min setup, ~4 min model load, ~8 min generation).

## What each cell does

| Section | Does |
|---|---|
| 0. Setup | Install dependencies, silence noisy logs |
| 1. Load Linguini | Pull 8 problems from the Hub (fixed seed, so every model sees the same ones) |
| 2. Load the model | Qwen2.5-14B-Instruct-AWQ, ~10 GB VRAM on a T4 |
| 3. Prompt & parser | System prompt + the `FINAL ANSWERS:` parser |
| 4. One problem, end to end | See a full raw generation next to the parsed answer |
| 5. Generate | Run the model on all 8 problems (**no scoring** — outputs stored in `generations`) |
| 6. Inspect | Read any raw generation |
| 7. Score | Exact-match + chrF vs the references (scores the stored generations, no re-run) |
| 8. Summary | Average scores and projected runtime vs the 30-min budget |

## Notes

- **Model choice:** a 14B model fits the T4 only quantized. Thinking models were ruled out — they blow the 30-min budget with reasoning tokens. See the notebook for details.
- **Real submissions:** the competition sandbox runs offline and cannot load AWQ/GPTQ. Ship full-precision weights and load them in 4-bit with `bitsandbytes` (commented variant in section 2).
- **Data:** please do not re-host Linguini problems in plaintext (contamination risk) — the notebook loads them from the Hub only.
