# RAG Evaluation Pipeline — Danske Bank 2024 Annual Report

A complete, reproducible pipeline that builds a Retrieval-Augmented Generation (RAG) system over Danske Bank's 2024 Annual Report and evaluates its quality using [RAGAS](https://github.com/explodinggradients/ragas).

## What's inside

| Step | Description |
|------|-------------|
| 1 | Install dependencies |
| 2 | Load OpenAI API key |
| 3 | Download Danske Bank 2024 Annual Report (PDF) |
| 4 | Load & chunk the PDF with explanation of chunking strategy |
| 5 | Build a local FAISS vector store |
| 6 | Build the RAG chain with a grounded system prompt |
| 7 | Define 5 evaluation questions with ground-truth answers |
| 8 | Run the pipeline on all questions |
| 9 | Evaluate with RAGAS (Context Precision, Recall, Faithfulness, Answer Relevancy) |
| 10 | Visualise scores with a colour-coded bar chart |
| 11 | Diagnostic section — what low scores mean and how to fix them |
| 12 | A/B experiment — compare chunk_size 800 vs 1600 |

## Results

### Baseline (chunk_size = 800)

| Metric | Score |
|--------|-------|
| Faithfulness | 1.000 |
| Context Recall | 0.850 |
| Answer Relevancy | 0.935 |
| Context Precision | 0.617 |

### A/B experiment delta (1600 − 800)

| Metric | Change |
|--------|--------|
| Context Precision | +0.161 |
| Context Recall | +0.100 |
| Answer Relevancy | +0.024 |
| Faithfulness | −0.200 |

Larger chunks improve retrieval quality but introduce a faithfulness tradeoff. See the Conclusion cell in the notebook for a full discussion.

## Setup

```bash
pip install -r requirements.txt
```

Then open `project.ipynb` in Jupyter or VS Code and run cells top to bottom.

You will need an [OpenAI API key](https://platform.openai.com/api-keys). Estimated cost to run the full notebook: **< $0.25**.

## Models used

- Embeddings: `text-embedding-3-small`
- LLM: `gpt-4o-mini`
