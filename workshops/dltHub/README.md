# README

## Overview

This project involves creating a Large Language Model (LLM) chatbot using various modern technologies for data ingestion, storage, and retrieval. The technologies used include Data Load Tool (DLT) for data ingestion, LanceDB as the vector database, and Ollama for Retrieval-Augmented Generation (RAG).

## Technologies Used

### 1. Data Load Tool (DLT)
DLT is used for data ingestion and provides the following capabilities:
- **Connecting to REST APIs**: DLT can easily connect to any REST API source, enabling dynamic data ingestion.
- **Seamless Integration**: It integrates smoothly with vector databases like LanceDB.
- **Incremental Loading**: DLT supports incremental loading, making it adaptable to dynamic data and schema changes without disrupting pipelines.

### 2. LanceDB
LanceDB is an open-source vector database that offers the following features:
- **Vector Embeddings Storage**: LanceDB is designed to store and manage vector embeddings efficiently.
- **Python Integration**: It integrates seamlessly into Python workflows, making it easy to use within the project.

### 3. Ollama
Ollama is an open-source tool that supports Retrieval-Augmented Generation (RAG) and allows running LLMs locally. This provides the following advantages:
- **Local LLM Execution**: Run large language models locally for efficient and secure processing.
- **RAG Capability**: Ollama enhances the chatbot's ability to retrieve and generate relevant responses based on vector searches.

## Concepts

### Embeddings
Embeddings are numerical representations of data that capture essential patterns and relationships within the data. They are used to transform high-dimensional data into lower-dimensional vectors.

### Vector Embeddings
Vector embeddings represent data as high-dimensional vectors. These vectors encode semantic information about the data, enabling similarity searches.

### Vector Search
Vector search involves finding vectors that are similar to a given query vector. It is used in applications like semantic search, where the goal is to find documents or items that are semantically similar to the query.

### Vector Databases
Vector databases are specialized databases designed to store and manage vector embeddings. They enable efficient storage, retrieval, and manipulation of high-dimensional vectors.

## Workshop: Open Source Data Ingestion for RAGs with DLT

In this hands-on workshop, we’ll learn how to build a data ingestion pipeline using DLT to load data from a REST API into LanceDB so you can have an always up-to-date RAG.

### Steps Covered:
1. **Extract Data from REST APIs**: Using DLT to fetch data from various REST API sources.
2. **Loading and Vectorizing into LanceDB**: Unlike other vector databases, LanceDB stores both the data and the embeddings.
3. **Incremental Loading**: Implementing incremental data loading to keep the database up to date without full reloads.

By the end of this workshop, you’ll be able to write a portable, open-source data pipeline for your RAG that you can deploy anywhere, such as Python notebooks, virtual machines, or orchestrators like Airflow, Dagster, or Mage.

### Resources
- **Video Tutorial**: [Watch the workshop](https://www.youtube.com/watch?v=qUNyfR_X2Mo)
- **Slides**: [dlt-LLM-Zoomcamp.pdf](https://github.com/user-attachments/files/16131729/dlt.LLM.Zoomcamp.pdf)
- **Google Colab Notebook**: [Follow along on Colab](https://colab.research.google.com/drive/1nNOybHdWQiwUUuJFZu__xvJxL_ADU3xl?usp=sharing)

## Project Structure

1. **Data Ingestion**:
   - Use DLT to connect to REST API sources and ingest data.
   - Perform incremental loading to adapt to dynamic data changes.

2. **Vector Storage**:
   - Store the ingested data as vector embeddings in LanceDB.
   - Manage and retrieve vector embeddings efficiently.

3. **Chatbot Implementation**:
   - Utilize Ollama to run LLMs locally and enable Retrieval-Augmented Generation (RAG).
   - Integrate the chatbot with LanceDB to perform vector searches and generate relevant responses.

## Getting Started

### Prerequisites
- Python 3.x
- DLT
- LanceDB
- Ollama

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-repo/llm-chatbot.git
   cd llm-chatbot
   ```

2. Install the required packages:
   ```bash
   pip install dlt lancedb ollama
   ```

### Usage

1. **Data Ingestion**:
   - Configure DLT to connect to your REST API source.
   - Ingest data and store vector embeddings in LanceDB.

2. **Run Chatbot**:
   - Use Ollama to load and run the LLM locally.
   - Implement vector search and RAG to generate responses.

### Example

Here's a basic example of how to use the technologies together:

```python
import dlt
import lancedb
import ollama

# Data Ingestion with DLT
data_source = dlt.load_source('api_endpoint', incremental=True)
data = dlt.ingest(data_source)

# Store Vector Embeddings in LanceDB
db = lancedb.connect('path/to/database')
embeddings = db.store_embeddings(data)

# Run LLM with Ollama for RAG
llm = ollama.load_model('path/to/model')
response = ollama.generate_response(llm, query='Your query here', embeddings=embeddings)

print(response)
```
