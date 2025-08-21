## LangSphere – AI Researcher (LangGraph + LangChain + Gemini + Streamlit)

Build and experiment with AI research agents that:
- **Search arXiv**, read PDFs, and **summarize/extract** content
- Generate a **LaTeX research paper** and export to **PDF**
- Provide an **interactive Streamlit chat UI**

### Features
- **Agentic workflow** with LangGraph + LangChain tools
- **arXiv search** tool with robust parsing
- **PDF reader** using PyPDF2
- **LaTeX → PDF** rendering via Tectonic
- **Streamlit UI** for conversational control

---

## Quick Start

### Prerequisites
- Python ≥ 3.11
- uv (Python package manager): see `https://astral.sh/uv/`
- Tectonic (LaTeX engine) for PDF export: `https://tectonic-typesetting.github.io/`
  - Windows: `winget install Tectonic.Tectonic`

### 1) Install deps
```bash
uv sync
```

### 2) Set environment variables
Create a `.env` file in the project root:
```bash
GOOGLE_API_KEY=your_google_gemini_api_key
```

### 3) Run the Streamlit app
```bash
uv run streamlit run frontend.py
```

- Default URL: `http://localhost:8501`
- Start chatting about a research topic. The agent will search arXiv, read PDFs, and draft a paper.

### 4) (Optional) Run from CLI
Basic interactive loop:
```bash
uv run python ai_researcher.py
```

---

## Project Structure

- `frontend.py`: Streamlit chat UI (imports `INITIAL_PROMPT`, `graph`, `config` from `ai_researcher_2.py`)
- `ai_researcher.py`: Simple CLI loop to interact with the agent
- `ai_researcher_2.py`: LangGraph state machine and agent wiring
- `arxiv_tool.py`: ArXiv search tool (query + XML parsing)
- `read_pdf.py`: PDF text extraction tool
- `write_pdf.py`: LaTeX → PDF rendering tool (requires Tectonic)
- `pyproject.toml`: Project metadata and dependencies (uv)
- `README.md`: This file

---

## Configuration

- Update the initial system prompt in:
  - `ai_researcher.py` → `INITIAL_PROMPT`
  - `ai_researcher_2.py` → `INITIAL_PROMPT`
- Make sure `GOOGLE_API_KEY` is set in `.env`.

---

## Troubleshooting

- **PDF not generated**
  - Ensure Tectonic is installed and available in PATH
  - Windows: `winget install Tectonic.Tectonic`
- **arXiv request failed**
  - Check your network and try a simpler query
- **Streamlit port in use**
  - `uv run streamlit run frontend.py --server.port 8502`
- **Gemini auth errors**
  - Verify `GOOGLE_API_KEY` in `.env`

---

## Tech Stack

- **LangGraph**, **LangChain**, **Google Gemini (langchain-google-genai)**
- **Streamlit**, **PyPDF2**, **Tectonic**
- **uv** for dependency and environment management

---

## Development

### Common uv commands
```bash
# Sync env
uv sync

# Run the app
uv run streamlit run frontend.py

# Run CLI
uv run python ai_researcher.py
```

---

## License
Apache-2.0 (see `LICENSE`)

---

## Repository
`https://github.com/Siddhantp08/LangSphere`
