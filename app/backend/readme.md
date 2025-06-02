# Backend Documentation

This backend powers the RAG (Retrieval Augmented Generation) chat app, enabling ChatGPT-like experiences over your own documents using Azure OpenAI Service and Azure AI Search.

## Overview

- **Language:** Python (3.9, 3.10, or 3.11)
- **Purpose:** Exposes APIs for chat and Q&A over indexed documents.
- **Key Azure Services:**
  - Azure OpenAI (GPT models)
  - Azure AI Search (document indexing and retrieval)
  - Optional: Azure Cosmos DB, Azure Blob Storage, Application Insights

## Features

- Multi-turn chat and single-turn Q&A endpoints
- Citation and source rendering for answers
- Settings to tweak RAG behavior
- Support for document ingestion and vectorization
- Optional: Vision (GPT-4V), speech, authentication, persistent chat history

## Project Structure

```
app/
  backend/
    ├── main.py           # Entry point (FastAPI app)
    ├── api/              # API route definitions
    ├── services/         # Azure service integrations
    ├── data/             # Data ingestion and processing
    ├── utils/            # Utility functions
    └── ...               # Other supporting modules
```

## Local Development

1. **Install dependencies:**
   ```shell
   pip install -r requirements.txt
   ```

2. **Set environment variables:**  
   Copy `.env.example` to `.env` and fill in your Azure resource keys and endpoints.

3. **Run the backend:**
   ```shell
   uvicorn main:app --reload
   ```

4. **Access the API:**  
   Default: [http://127.0.0.1:8000](http://127.0.0.1:8000)

## Deployment

The backend is deployed as part of the full app using Azure Developer CLI (`azd up`).  
See the root [README](../../README.md) for full deployment instructions.

## Environment Variables

- `AZURE_OPENAI_ENDPOINT`
- `AZURE_OPENAI_KEY`
- `AZURE_SEARCH_ENDPOINT`
- `AZURE_SEARCH_KEY`
- (Optional) `AZURE_COSMOSDB_CONNECTION_STRING`, `AZURE_STORAGE_CONNECTION_STRING`, etc.

## API Endpoints

- `POST /chat` — Chat with your data (multi-turn)
- `POST /qa` — Single-turn Q&A
- `GET /health` — Health check

See [OpenAPI docs](http://127.0.0.1:8000/docs) when running locally.

## Testing

To run backend tests:
```shell
pytest
```

## Additional Resources

- [Azure OpenAI Service Documentation](https://learn.microsoft.com/azure/cognitive-services/openai/)
- [Azure AI Search Documentation](https://learn.microsoft.com/azure/search/)
- [Project Root README](../../README.md)

---

**Note:** This backend is for demonstration purposes. For production use, review and implement additional security and operational best practices.