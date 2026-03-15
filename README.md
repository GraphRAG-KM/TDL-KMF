# TDL-KMF - Tactical Data Link Knowledge Modeling Framework

TDL-KMF is a Tactical Data Link Knowledge Modeling Framework designed to support knowledge extraction, ontology construction, and model generation for tactical data link domains. Based on GraphRAG and related intelligent information processing technologies, it can automatically extract domain knowledge from PDF documents and generate OWL ontologies and UML models. It integrates text extraction, OCR recognition, graph construction, inference, and other technologies to provide users with a one-stop knowledge modeling and ontology generation solution for tactical data link systems.

## Features

- **PDF Document Processing and Text Extraction**: Supports extracting text from PDF documents to obtain key domain information related to tactical data links.
- **Image OCR Recognition**: Supports text extraction from images, helping recognize content from scanned documents, technical manuals, or pictures.
- **GraphRAG-Based Knowledge Graph Construction**: Automatically constructs tactical data link knowledge graphs and visualizes domain knowledge in graph form.
- **Entity and Relationship Inference**: Infers entities and their relationships from extracted text and images to build a more complete domain knowledge graph.
- **Automatic OWL Ontology Generation**: Automatically constructs OWL ontology from extracted information, supporting semantic reasoning and knowledge storage in the tactical data link domain.
- **Automatic StarUML Class Diagram Generation**: Converts ontology structures into UML class diagrams for easy visualization and editing.

## Installation

```bash
pip install GraphragKM
```

## Usage

### Command Line Usage

```bash
# Interactive run
graphragkm run

# Specify input file
graphragkm run -i input.pdf
```

### Generated Files

After execution, the program will generate the following files in the `output` folder in the current directory:

- `ontology.owl`: The generated OWL ontology file.
- `uml_model.puml`: The UML class diagram file (StarUML format).

### Configuration

On the first run, the program will create a `config.yaml` configuration file template in the current directory. You need to edit this file and fill in the correct API keys and other configuration information.

```yaml
api:
  # Mineru API settings
  mineru_upload_url: "https://mineru.net/api/v4/file-urls/batch"
  mineru_results_url_template: "https://mineru.net/api/v4/extract-results/batch/{}"
  mineru_token: "YOUR_MINERU_TOKEN"

  # Chat model settings
  chat_model_api_key: "YOUR_CHAT_MODEL_API_KEY"
  chat_model_api_base: "https://api.deepseek.com"
  chat_model_name: "deepseek-chat"

  # Embedding model settings
  embedding_model_api_key: "YOUR_EMBEDDING_MODEL_API_KEY"
  embedding_model_api_base: "https://open.bigmodel.cn/api/paas/v4/"
  embedding_model_name: "embedding-3"

app:
  # OWL Namespace
  owl_namespace: "https://example.com/"

  # Maximum concurrent requests
  max_concurrent_requests: 25
```

## Development Layout

Project source modules now live directly under `src/`, with configuration code kept in `src/config/`.
The main pipeline entry module is `src/app_main.py`, while the repository-root `main.py` remains available as a convenience launcher for `python main.py`.

## Dependencies

- Python 3.11+
- graphrag
- easyocr
- openai
- pandas
- rdflib
- rich
- click
- scikit-learn
- For a full list of dependencies, see `pyproject.toml`
