# RAG-and-LangChain

Minimal RAG walkthrough using LangChain, Google Generative AI (Gemini), and Chroma.

## Prerequisites
- Python 3.11+
- Google Generative AI API key (`GOOGLE_API_KEY`)
- Git (if you plan to push to GitHub)

## Setup
1) Create a virtual environment (recommended):
```bash
python3 -m venv .venv
source .venv/bin/activate
```
2) Install dependencies:
```bash
pip install langchain langchain-google-genai langchain-text-splitters langchain-community chromadb nltk ipython pypdf
```
3) Set your API key (choose one):
- Terminal: `export GOOGLE_API_KEY="your-api-key"`
- Or in the notebook: `os.environ["GOOGLE_API_KEY"] = "your-api-key"`

## Running the notebook
Open `code.ipynb` and run cells in order:
- Install deps (if not already installed)
- Download NLTK data (`punkt_tab`)
- Download the sample PDF (`ai_pv.pdf`)
- Load/split text into chunks
- Embed and store in Chroma (persisted in `./chroma_db_ai_pv`)
- Query via the RAG chain

## Notes on Google GenAI quotas
- Free tier has strict per-minute and per-day limits for embeddings. If you hit `ResourceExhausted` / quota errors, wait for reset, reduce batch size (e.g., 4), embed fewer chunks, or enable billing to raise limits.

## Pushing to GitHub (quick ref)
```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin <your-repo-url>
git push -u origin main
```

## Project layout
- `code.ipynb` — main notebook with the RAG pipeline
- `ai_pv.pdf` — sample document used for ingestion
- `chroma_db_ai_pv/` — persisted Chroma vector store

