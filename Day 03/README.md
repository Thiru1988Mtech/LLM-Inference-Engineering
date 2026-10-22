# Day 03: Embeddings

Token IDs carry no meaning. The embedding layer fixes that with a **lookup table**: row *i* is the vector for token *i*.

## What you will learn
- Embedding as a row lookup, and why it equals a one-hot matrix multiply
- How GPT-2 adds learned position vectors, and how RoPE encodes relative position
- Nearest neighbours and PCA to see structure in the vectors
- How big embedding tables are for real models

## Notebook outline
1. An embedding is a table lookup
2. Position: the second table
3. Is there meaning in the geometry?
4. Beyond a learned table: RoPE
5. Embedding tables and memory

## Run it
```bash
python3 -m venv ../.venv && source ../.venv/bin/activate     # Windows: ..\.venv\Scripts\activate
pip install -r requirements.txt
jupyter notebook Day03_Embeddings.ipynb
```
Reuses the GPT-2 weights file from Day 02 (downloads it if missing). No GPU needed.

## Files
| File | Purpose |
|------|---------|
| `Day03_Embeddings.pptx` | Slides for the video |
| `Day03_Embeddings.ipynb` | Notebook, run top to bottom |
| `requirements.txt` | Python dependencies |

## Key takeaways
- Embedding = row lookup in a [vocab, hidden] table.
- Position is added (GPT-2) or rotated in (RoPE).
- Nearby vectors are related tokens.

**Next: Day 04**, Attention.
