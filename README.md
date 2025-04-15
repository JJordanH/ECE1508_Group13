# ECE1508 Group 13 — Retrieval-Augmented Generation with Adaptive Chunking

This is the official GitHub repository for **ECE1508 Group 13** at the University of Toronto.  
**Project Title:** *Enhancing Retrieval-Augmented Generation with Adaptive Chunking*

---

## Overview

This project investigates how document chunking strategies—specifically token-based recursive chunking—impact the performance of Retrieval-Augmented Generation (RAG) systems. We evaluate the pipeline on the TriviaQA dataset using both local and remote LLMs.

---

## Repository Structure

### `Local_LLM_RAG_pipeline/`

This folder contains all code, notebooks, and outputs for the **local deployment** of the RAG pipeline using `LLama-3.2-3B-Instruct-AWQ`.

#### Notebooks

| Notebook Name              | Description                                                             |
|---------------------------|-------------------------------------------------------------------------|
| `explore.ipynb`           | Development and debugging of the RAG pipeline                           |
| `explore_test.ipynb`      | Pipeline testing with a smaller sample                                  |
| `eval.ipynb`              | Evaluation using 500-token chunks with RAG                              |
| `eval_250_token.ipynb`    | Evaluation using 250-token chunks with RAG                              |
| `eval_no_rag.ipynb`       | Evaluation without RAG (baseline)                                       |
| `pre_eval_250_token.ipynb`| Generate Knowledge base for 250 tokens per chunk                              |
| `prep-eval.ipynb`         | Generate Knowledge base for 500 tokens per chunk                          |

#### `test_results/`

Contains output files used for evaluation:
- Prediction and instance JSON files
- Organized for 500-token, 250-token, and no-RAG runs
- Compatible with the official TriviaQA evaluation script

#### `output/`

Contains raw terminal outputs from TriviaQA evaluation runs, showing final **Exact Match (EM)** accuracy.

---

### `Remote_LLM_RAG_pipeline/`

This folder contains code, notebooks, and examples of outputs for the **remote** of the RAG pipeline using `Remote_LLM_RAG_pipeline`. The code can run on Kaggle platform.

#### Notebooks

| Notebook Name              | Description                                                             |
|---------------------------|-------------------------------------------------------------------------|
| `Remote_LLM_RAG`           | Whole process of the RAG pipeline. You need to change some variebles and file paths for different cases (500-token, 250-token, and no-RAG runs)|
| `1508experiment.ipynb`      | Development and debugging of the RAG pipeline                                  |

#### `test_results/`

Contains output files examples:
- Prediction and instance JSON files for the first 100 questions

#### `output/`

Contains raw terminal outputs from TriviaQA evaluation runs, showing final **Exact Match (EM)** accuracy. 

---

## Evaluation

All evaluations were run using the official TriviaQA evaluation script.  
Each configuration was tested on a consistent subset of the dataset.  
**Exact Match (EM)** is used as the key metric.

---

## System Details

- **Local LLM**: `LLama-3.2-3B-Instruct-AWQ` (via `vllm`) on an RTX 3080 (10GB VRAM)
- **Remote LLM**: `LLama-3.1-8B-Instruct-Turbo`
- **Embedding Model**: `GTE-small`
- **Retrieval**: FAISS using cosine similarity for top-`k` retrieval

---

