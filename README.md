# Relational RAG: Natural-Language Interface for DuckDB

A CLI tool that lets business users query a local DuckDB database in plain English — with inspectable, trustworthy results.

## The Problem

With so many dashboards available, business users often struggle to find the right information quickly. Existing natural-language-to-SQL systems are unreliable and hard to trust, leaving users uncertain whether the generated query is correct.

## What It Does

The user types a question in natural language (e.g. *"What were the top 5 products by revenue last quarter?"*). The system:

1. Retrieves relevant schema fragments and similar past queries using RAG.
2. Generates SQL with an LLM, grounded in that retrieved context.
3. Executes the SQL against a local DuckDB database.
4. Returns the query results, the generated SQL, a short plain-English explanation, and basic trust indicators (similar past queries, tables used).

The success metric is higher accuracy on a small benchmark of business questions compared to a no-retrieval baseline, plus consistent and inspectable outputs that help users understand and trust the answers.

## Setup

1. Install uv if you don't have it yet: https://docs.astral.sh/uv/getting-started/installation/

2. Clone this repository (or download the zip and extract it).

3. Create a `.env` file from the template and add your API key:

       cp .env.example .env

4. Install dependencies:

       uv sync

5. Start Jupyter:

       uv run jupyter notebook

## Notebooks

- `notebooks/01-setup.ipynb` - smoke test that confirms your environment works
- `notebooks/02-rag.ipynb` - a minimal RAG baseline you can adapt to your own data

## Data

Put your project data in the `data/` folder. See `notebooks/02-rag.ipynb` for how to load it.
