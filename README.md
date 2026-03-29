# Brand Guardian: Automated Compliance QA Pipeline

**Brand Guardian** is an AI-driven orchestration pipeline designed to automate the compliance auditing of video advertisements. By leveraging **Multimodal AI** and **RAG (Retrieval-Augmented Generation)**, the system extracts visual and auditory intelligence from videos and evaluates them against complex brand guidelines.

## Core Features

* **Multimodal Extraction**: Automated processing of YouTube/MP4 files to extract transcripts and OCR text using **Azure AI Video Indexer**.
* **Graph-Based Orchestration**: Managed state transitions and logic flow using **LangGraph**.
* **Intelligent Retrieval**: Vector-based search of compliance PDF documents using **Azure AI Search**.
* **Automated Auditing**: Context-aware compliance reporting powered by **GPT-4o**, identifying specific brand violations and misleading claims.

---

## Architecture

The system is built as a stateful graph where each node represents a specific stage of the audit process:

1. **Indexer Node**: Downloads video and triggers Azure Video Indexer for metadata extraction.
2. **RAG Node**: Queries a vector database for relevant brand rules based on video content.
3. **Auditor Node**: Synthesizes video insights and rules to generate a compliance verdict.
4. **Report Node**: Formats the final audit into a structured PDF/Text report.

---

## Tech Stack

* **Orchestration**: LangChain / LangGraph
* **Cloud Services**: Azure OpenAI, Azure AI Video Indexer, Azure AI Search
* **Package Management**: `uv` (Fast Python bundling)
* **Environment**: Python 3.10+
* **APIs**: FastAPI (Backend structure)

---

## Prerequisites

Before running the pipeline, ensure you have:

* An **Azure Subscription** with OpenAI, Video Indexer, and Search services enabled.
* **Python 3.10+** installed.
* The `uv` package manager installed (`pip install uv`).

---

## Setup & Installation

### 1. Clone the Repository

```bash
git clone https://github.com/abdulraafaykhan/Compliance_QA_Pipeline.git
cd Compliance_QA_Pipeline

```

### 2. Configure Environment Variables

Create a `.env` file in the root directory based on the `.env.example` provided:

```bash
cp .env.example .env
# Open .env and add your Azure Credentials

```

### 3. Install Dependencies

Using `uv` for lightning-fast installation:

```bash
uv sync

```

---

## Usage

To start the compliance audit for a YouTube video:

```bash
uv run python main.py

```

---

## Project Structure

```text
├── backend/
│   ├── data/             # Compliance PDF guidelines
│   ├── scripts/          # Document indexing utilities
│   └── src/
│       ├── api/          # FastAPI server logic
│       ├── graph/        # LangGraph nodes and state definitions
│       └── services/     # Azure Video Indexer & Search clients
├── main.py               # Entry point for the pipeline
├── pyproject.toml        # Dependency definitions
└── .env.example          # Environment template



