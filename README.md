# Book Recommendation System

This project implements a book recommendation system using embeddings, vector database, and LLM for generating responses to user queries. The system processes a book dataset, generates embeddings for each book, stores them in a FAISS vector database, and uses an LLM to generate natural language responses to user queries about books.

## Features

- **Data Processing**: Load and preprocess book data from CSV files
- **Embedding Generation**: Generate embeddings for books using BAAI's embedding model
- **Vector Database**: Store and search book embeddings using FAISS
- **Query Processing**: Process user queries and generate responses using LLM
- **API**: Expose the recommendation system through a FastAPI interface

## Project Structure

```
movie-recommendations/
├── movie-reommendations/
│   ├── data/
│   │   ├── book_dataset.csv       # Book dataset
│   │   ├── embeddings.npz         # Generated embeddings (created on first run)
│   │   ├── faiss_index.bin        # FAISS index (created on first run)
│   │   └── book_indices.npy       # Book indices (created on first run)
│   └── src/
│       ├── data_processing/       # Data loading and preprocessing
│       ├── embedding/             # Embedding generation
│       ├── vector_db/             # Vector database management
│       ├── llm/                   # LLM query processing
│       ├── api/                   # API interface
│       └── main.py                # Main script
├── .env                           # Environment variables
├── Makefile                       # Build and run commands
├── requirements.txt               # Dependencies
└── README.md                      # This file
```

## Installation

1. Clone the repository
2. Install dependencies:

```bash
make install
```

## Usage

### Interactive Mode

Run the system in interactive mode:

```bash
make run
```

### Single Query

Run with a specific query:

```bash
make query q="Recommend me a fantasy book with strong female characters"
```

### API Server

Start the API server:

```bash
make run-api
```

Then access the API at http://localhost:8000/docs

### Rebuild Embeddings

Force rebuilding of embeddings and index:

```bash
make rebuild
```

## Environment Variables

The following environment variables can be set in the `.env` file:

- `open_api_key`: API key for the LLM service
- `BOOK_DATA_PATH`: Path to the book dataset CSV file
- `EMBEDDINGS_PATH`: Path to save/load embeddings
- `INDEX_PATH`: Path to save/load FAISS index
- `METADATA_PATH`: Path to save/load book indices

## API Endpoints

- `POST /recommend`: Recommend books based on a user query
- `GET /health`: Health check endpoint

## Dependencies

- Python 3.8+
- NumPy
- Pandas
- FAISS
- PyTorch
- Transformers
- FastAPI
- Uvicorn

## License

This project is licensed under the MIT License - see the LICENSE file for details.