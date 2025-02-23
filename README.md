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
