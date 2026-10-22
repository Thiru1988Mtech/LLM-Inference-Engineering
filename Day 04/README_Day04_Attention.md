# Day 04 — Attention in LLMs

**Series:** LLM Inference Engineering  
**Lesson:** Day 04 — Attention  
**Notebook:** `Day04_Attention_HandsOn_Notebook.ipynb`

## Learning objectives

By the end of this lesson, you should be able to:

1. Explain the roles of Query, Key, and Value (Q, K, V).
2. Calculate attention scores and apply Softmax to obtain attention weights.
3. Combine Value vectors using attention weights.
4. Explain why causal masking blocks future token positions.
5. Compare MHA, GQA, and MQA in terms of Key-Value heads and cache memory.
6. Explain why attention scores are scaled by the square root of the key dimension.
7. Demonstrate why the full attention score matrix grows quadratically with sequence length.
8. Describe how FlashAttention reduces memory traffic without making exact full attention linear in sequence length.

## Project structure

Save both files inside your existing `Day 04` folder:

```text
LLM Inference Engineering/
├── Day 03/
└── Day 04/
    ├── README.md
    └── Day04_Attention_HandsOn_Notebook.ipynb
```

If you downloaded this file with the name `README_Day04_Attention.md`, rename it to `README.md` after placing it in the `Day 04` folder. If a `README.md` already exists there, keep it and merge these lesson notes rather than overwriting your existing content.

## Requirements

The notebook uses:

- Python
- NumPy
- Matplotlib
- Jupyter support in VS Code

The first setup cell installs NumPy and Matplotlib if they are missing from the selected Python environment.

## How to run in VS Code

1. Open `Day04_Attention_HandsOn_Notebook.ipynb`.
2. Select the Python kernel for your project, preferably the project's `.venv`.
3. Run cells from top to bottom.
4. Read each Markdown explanation before running the code.
5. Use the recording script in each section to explain the output in simple English.

## Lesson workflow

**Understand → Run code → Observe visualization → Explain in your own words → Record**

The notebook uses small illustrative numbers for learning. It does not load a full language model and does not require a GPU.

## Lesson outline

1. Setup and imports
2. Query, Key, and Value
3. Attention score matrix
4. Softmax weights
5. Weighted Value combination
6. Causal mask
7. MHA, GQA, and MQA cache comparison
8. Scaling by the square root of the key dimension
9. Quadratic context-length growth
10. Context-length mini experiment
11. Knowledge check and answers
12. Day 04 recap

## Key formulas

Scaled dot-product attention:

`Attention(Q, K, V) = softmax(Q Kᵀ / √dₖ) V`

Illustrative KV-cache size per token:

`2 × number_of_layers × number_of_KV_heads × head_dimension × bytes_per_value`

The factor `2` accounts for both Keys and Values. Exact memory use depends on the model, data type, cache layout, and serving implementation.

## Important note about the attention matrix

The full attention score matrix has `sequence_length × sequence_length` entries. Doubling sequence length makes this matrix four times as large. FlashAttention reduces memory traffic and avoids materializing the full score matrix, while exact full attention still has quadratic arithmetic complexity.

## Next lesson

**Day 05 — KV Cache**
