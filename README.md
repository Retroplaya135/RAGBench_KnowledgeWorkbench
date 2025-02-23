# RAGBench_KnowledgeWorkbench

AI Knowledge Workbench 2025

Enterprise RAG System for Developers
A next-gen Retrieval-Augmented Generation (RAG) system that unifies vector search, knowledge graphs, and LLM-powered insights—all in an enterprise-ready platform tailored for complex developer workflows.

Overview

AI Knowledge Workbench 2025 is an advanced Retrieval-Augmented Generation (RAG) framework that combines:

* Multi-source ingestion (codebases, documents, web, media).
* Hybrid retrieval (Weaviate vector search + LlamaIndex knowledge graph).
* LLM-powered code analysis and codebase understanding.
* Collaboration tools for real-time knowledge sharing and annotation.
* Enterprise-ready features like auditing, RBAC, data lineage tracking, and plugin-based extensibility.

Installation

* Prerequisites
* Python 3.9+
* Weaviate (Can use Embedded Weaviate or a remote instance)
* Virtual Environment recommended

# Clone the repository
```
git clone https://github.com/your-org/ai-knowledge-workbench-2025.git
cd ai-knowledge-workbench-2025
```

# Create and activate a virtualenv
```
python3 -m venv venv
source venv/bin/activate  # Linux/Mac
venv\Scripts\activate     # Windows
```

# Install Python dependencies
```
pip install -r requirements.txt
```
* Additional Dependencies
* Install libpq-dev, build-essential or other system-level dependencies if required by Weaviate or external libraries.
* For GPU-based LLM backends, ensure CUDA drivers and libraries are installed.

Configuration

The system uses environment variables for advanced features:

COHERE_API_KEY: (Optional) For cross-encoder re-ranking or Cohere embedding.
HF_API_KEY: (Optional) For Hugging Face-based re-ranking or embeddings.
WEAVIATE_HOST: Host endpoint for Weaviate if not using embedded mode.
WEAVIATE_PORT: Port for Weaviate if not using embedded mode.

You can store these in a .env file or inject them through your CI/CD pipeline:

```
export COHERE_API_KEY="<your-cohere-key>"
export HF_API_KEY="<your-hf-key>"
```

Quick Start

Launch Weaviate (optional if using embedded)


```
docker run -d --name weaviate \
    -p 8080:8080 \
    semitechnologies/weaviate:latest
```

Open GUI
* The system automatically opens a Tkinter-based GUI (requires a graphical environment).
* Add codebases or documents using the “Add Codebase” or “Add Documents” buttons.
* Query using the text box under Query Interface.

Plugin System

The Workbench supports a plugin architecture for extending ingestion, indexing, and retrieval capabilities:

Plugin Directory
Place Python modules in plugins/. Each plugin must implement a Plugin class with a constructor that takes the main RAGWorkbench object.
Typical Use Cases
Domain-specific chunkers for specialized file types (e.g., UML diagrams, large config files).
Custom re-rankers or classifiers for improved retrieval.
Collaboration integrations (e.g., Slack, MS Teams).
Security plugins (custom RBAC policies, advanced encryption at rest).

```
class Plugin:
    def __init__(self, workbench):
        self.workbench = workbench
        # Perform plugin initialization
        print("My Plugin is active!")

    def on_document_ingested(self, documents):
        # Optional hook for post-ingestion processing
        pass

    def on_query(self, query_text):
        # Optional hook to transform or log queries
        pass
```

Collaboration & RBAC

* Real-Time Chat & Annotation
* Embeds a developer chat that references specific code snippets or documents within the knowledge graph.
* Shared Knowledge Graph
* Multiple users can collaborate and see real-time updates to the KG.
* Access Control
* Role-Based Access Control (RBAC) ensures only authorized users can access sensitive documents or code sections.
* Audit logging captures ingestion, retrieval, and query usage data for compliance.
