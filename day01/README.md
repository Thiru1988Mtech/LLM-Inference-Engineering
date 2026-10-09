# Day 01: What Is LLM Inference?

An LLM does not plan an answer and then write it. It predicts **one token**, appends it, and predicts the next. That loop is inference.

## What you will learn
- The three stages of every request: tokenize, forward pass, decode
- What logits are, and how greedy, temperature, top-k and top-p pick a token
- How to write the autoregressive loop by hand and verify it against `model.generate()`
- The two latency metrics used all series: TTFT and TPOT

## Notebook outline
1. Training vs inference
2. Stage 1 — Tokenization: text to integers
3. Stage 2 — The forward pass: integers to scores
4. Stage 3 — Decoding: scores to one token
5. The autoregressive loop
6. What does it cost? Two numbers to know

## Run it
```bash
python3 -m venv ../.venv && source ../.venv/bin/activate     # Windows: ..\.venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook Day01_LLM_Inference_Mechanics.ipynb
```
GPT-2 (124M) from Hugging Face, about 500 MB on first run. No GPU needed.

## Files
| File | Purpose |
|------|---------|
| `Day01_What_Is_LLM_Inference.pptx` | Slides for the video |
| `Day01_LLM_Inference_Mechanics.ipynb` | Notebook, run top to bottom |
| `requirements.txt` | Python dependencies |

## Key takeaways
- Generation is one token at a time, in a loop.
- Naive steps get slower as the sequence grows.
- TTFT and TPOT are the metrics for the whole series.

**Next: Day 02**, What's Inside a Model.
