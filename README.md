# CulinaryChronicler: 1800s Recipes & Culinary Lexicon AI (LLaMA 3.1 8B)

## Project Overview

CulinaryChronicler is an AI-powered recipe bot specializing in 19th-century cuisine, featuring a historical recipe database and an English cooking dictionary. The project implements intelligent query routing, enabling efficient retrieval of culinary information and an extensive lexicon of cooking terminology.

### Key Technologies:
- LlamaIndex for indexing and querying
- Ollama LLaMA 3.1 8B as the primary language model
- BAAI/bge-small-en-v1.5 for embeddings
- ChromaDB as vector store
- LlamaParse API for parsing documents

## Prerequisites

- Python 3.8+
- Anaconda or Miniconda
- Git

## Installation

1. Clone the repository:

```
git clone https://github.com/CPotnis/CulinaryChronicler.git
cd CulinaryChronicler
```

2. Create and activate the Conda environment:
```
conda env create -f environment.yml
conda activate culinary-chronicler
```

3. Install Ollama:
- Follow the installation instructions at [https://ollama.ai/](https://ollama.ai/)
- Pull the LLaMA 3.1 8B model:
  ```
  ollama pull llama3.1
  ```

## Configuration

1. Create a `.env` file in the project root:
```
OPENAI_API_KEY=your_openai_api_key
LLAMA_CLOUD_API_KEY=your_llama_cloud_api_key`
```

2. Prepare your data:
- Place the cookbook PDF in `data/175_choice_recipes_mainly_furnished_by_members_of_the_chicago_womens_club-1887.pdf`
- Place the food dictionary PDF in `data/dictionary-of-food.pdf`

## Running the Project

1. Start Jupyter Notebook:
```
jupyter notebook
```
2. Open the notebook containing the project code.

3. Run each cell in order, ensuring to adjust file paths if necessary:
- Update `CHROMA_DB_PATH` if needed
- Verify `COOKBOOK_PATH` and `DICTIONARY_PATH` are correct
- Adjust `DICTIONARY_PICKLE_PATH` if desired

4. The final cell contains example queries. Modify or add new queries to interact with CulinaryChronicler.

## Project Structure

- `data/`: Contains cookbook and food dictionary PDFs
- `local_db_ollama/`: ChromaDB database files
- `raw_dictionary_documents`: Pickled processed dictionary data

## Key Functions

- `initialize_models()`: Sets up language and embedding models
- `load_dictionary_data()`: Loads or generates dictionary data
- `load_cookbook_data()`: Loads cookbook data from PDF
- `create_vector_store()`: Creates ChromaDB vector store
- `create_index()`: Creates vector store index from documents
- `create_query_engine()`: Creates query engine from index
- `create_query_engine_tools()`: Creates query engine tools for agent
- `create_agent()`: Creates agent with query engine tools
- `query_agent()`: Queries the agent with user input

## Usage

After running all cells, query CulinaryChronicler using:

```python
response = query_agent(agent, "What is aloo?")
print(response)

response = query_agent(agent, "How to prepare Marrow Dumpling Soup? Give me steps.")
print(response)
```

## Troubleshooting

- LlamaParse issues: Verify LLAMA_CLOUD_API_KEY in .env
- Ollama problems: Ensure proper installation and model download
- ChromaDB issues: Try deleting local_db_ollama/ and rerun cells

## Contributing
- Contributions welcome! Fork the repository and submit a pull request with your changes.
## License
This project is licensed under the MIT License - see the LICENSE file for details.