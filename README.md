# Custom MCP Server with RAG & Tools

This project implements a **Custom MCP (Multi-tool Control Protocol) server** using [FastMCP](https://github.com/multiprocessio/mcp), supporting:

* Notes Management (Add / Read / Summarize Notes)
* Weather Search (via WeatherAPI)
* Brave News Search (via Brave API)
* Document Ingestion & RAG Queries (via GroundX)
* OpenAI GPT Integration for Summarization & RAG

---

## Features

* Append, read, and summarize text notes locally
* Get real-time weather info
* Search current news headlines via Brave API
* Ingest PDFs and perform RAG-based semantic search using GroundX
* Supports OpenAI GPT (e.g., `gpt-4o`) for completions
* Local MCP Inspector for testing/debugging

---

## Installation

### 1. Using `uv` (Recommended)

```bash
uv lock
uv sync
```


### 2. Using pip

```bash
pip install -r requirements.txt
```

---

## Environment Variables (`.env`)

```dotenv
OPENAI_API_KEY=your_openai_api_key
GROUNDX_API_KEY=your_groundx_api_key
WEATHER_API_KEY=your_weatherapi_key
BRAVE_API_KEY=your_brave_api_key
BUCKET_ID=your_groundx_bucket_id
```

---

## Running the MCP Server

### Development Mode (with Inspector UI)

```bash
mcp dev main.py
```

If you get authentication errors, run with:

```bash
DANGEROUSLY_OMIT_AUTH=true mcp dev main.py
```
### Development Mode with claude desktop app:

```bash
mcp install main.py
mcp run main
```

---

## Available Tools & Resources

| Tool Name                       | Description                                    |
| ------------------------------- | ---------------------------------------------- |
| `add_note(message)`             | Append note to local file                      |
| `read_notes()`                  | Return all stored notes                        |
| `note_summary_prompt()`         | Generate a prompt to summarize notes using GPT |
| `brave_search_results(q)`       | Latest news via Brave Search API               |
| `fetch_weather(city)`           | Real-time weather from WeatherAPI              |
| `ingest_documents(path)`        | Upload PDF to GroundX knowledge base           |
| `process_search_query(q)`       | Perform RAG search with OpenAI GPT completions |
| `search_doc_for_rag_context(q)` | Retrieve context text for GPT queries          |

---

## API Example (via Inspector)

```json
{
  "tool": "fetch_weather",
  "args": {
    "city": "New York"
  }
}
```

---

## Example Workflow

```bash
uv sync
cp .env.example .env  # setup .env file
mcp dev main.py       # start MCP development server
```

---

## Troubleshooting

**Error:** `Connection Error - Missing Proxy Token`

➡️  Solution: Use the URL provided or run:

```bash
DANGEROUSLY_OMIT_AUTH=true mcp dev main.py
```


## License

MIT License
© 2025 Your Name / Your Organization

---

Generated with ❤️ using MCP, GroundX, OpenAI.
