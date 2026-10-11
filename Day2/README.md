# Day 02: What's Inside a Model

A model file is not a program. It is a **container of named arrays**, and the tokenizer is a lookup table with merge rules. Today we open both, with no ML framework.

## What you will learn
- The `.safetensors` layout: 8-byte length, JSON header, raw numbers
- Where GPT-2's 124M parameters live, and how to predict the count from `config.json`
- Why parameters x bytes per parameter decides your GPU memory
- Byte-level BPE built from scratch and verified against Hugging Face
- How token counts differ across languages and content types

## Notebook outline
**`Day02_Whats_Inside_A_Model.ipynb`**
1. What is inside a model file?
2. Get GPT-2's files
3. Read the blueprint: `config.json`
4. Parse `.safetensors` by hand
5. Inventory: learned weights vs constant buffers
6. Where do the parameters live?
7. Look at real weight values
8. Weights decide your GPU memory bill

**`Day02_Tokenization.ipynb`**
1. Setup: only the small tokenizer files
2. Why subwords?
3. Why tokenization matters for inference
4. Bytes as printable characters
5. Pre-tokenization, then merging
6. Check against the official implementation


## Run it
```bash
python3 -m venv ../.venv && source ../.venv/bin/activate     # Windows: ..\.venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook Day02_Whats_Inside_A_Model.ipynb
jupyter notebook Day02_Tokenization.ipynb
```
Downloads GPT-2 files from Hugging Face (about 550 MB for the first notebook, 1.5 MB for the second). No GPU needed.

## Files
| File | Purpose |
|------|---------|
| `Day02_Whats_Inside_A_Model.pptx` | Slides for the video |
| `Day02_Whats_Inside_A_Model.ipynb` | Notebook, run top to bottom |
| `Day02_Tokenization.ipynb` | Notebook, run top to bottom |
| `requirements.txt` | Python dependencies |

## Key takeaways
- A checkpoint is a JSON header plus raw numbers.
- Parameters x bytes decides the memory you need.
- Fewer tokens per request means faster, cheaper inference.

**Next: Day 03**, Embeddings.
