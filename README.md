# Weather AI Assistant

## Project Overview

This project presents an intelligent weather assistant that combines large language models, tool use, retrieval-augmented generation (RAG), corrective retrieval (CRAG), conversational memory, and multi-step reasoning using the ReAct framework.

The system is designed to handle different types of weather-related queries. It can retrieve real-time weather data using an external API, perform temperature conversions, answer date and time questions, and provide knowledge-based responses from weather-related documents.

Instead of relying on a single-step decision, the assistant uses an agent-based architecture enhanced with ReAct reasoning, allowing it to think, act, and refine its decisions across multiple steps.

---

## Main Features

The system supports the following capabilities:

- Real-time weather retrieval using the Open-Meteo API  

- Temperature conversion between Celsius and Fahrenheit  

- Date and time responses  

- Knowledge-based question answering using RAG  

- Corrective retrieval using CRAG to improve retrieval quality  

- Multi-step reasoning using the ReAct framework  

---

## System Architecture

The project is built around an LLM-based agent enhanced with ReAct reasoning.

### Workflow:

1. The user submits a query  

2. The system resolves the query using conversational memory (if needed)  

3. The agent performs reasoning (Thought)  

4. The agent selects an action (tool)  

5. The tool is executed (Observation)  

6. The agent may refine its reasoning if needed  

7. The final response is generated  

### Available Tools:

- `weather_api`  

- `weather_and_convert`  

- `converter`  

- `date_time`  

- `rag`  

---

## Why Agentic RAG with ReAct

A standard RAG pipeline is suitable only for document-based questions. However, this project includes multiple types of queries:

- Some require retrieval from documents (e.g., explanations)  

- Some require real-time data (e.g., current weather)  

- Some require computation (e.g., temperature conversion)  

Initially, the system used a **single-step agent decision**, where the model selected a tool and executed it directly.

However, this approach had limitations:

- No intermediate reasoning  

- Limited flexibility for complex queries  

- No refinement after tool execution  

To address this, we enhanced the system using the **ReAct (Reasoning + Acting) framework**.

### Benefits of ReAct:

- Enables step-by-step reasoning (Thought → Action → Observation)  

- Allows the agent to make more informed decisions  

- Improves handling of complex or multi-part queries  

- Provides better transparency in decision-making  

---

## Retrieval Pipeline

The knowledge component of the project was initially built as a standard RAG pipeline. The pipeline includes:

- Loading documents from different file types  

- Extracting and cleaning text  

- Splitting documents into chunks  

- Generating embeddings  

- Storing embeddings in a vector database  

- Retrieving the most relevant chunks for a given query  

### Document Sources:

- PDF files  

- Markdown files  

- HTML / web pages  

---

## Embeddings and Vector Storage

Document chunks are converted into embeddings using a sentence-transformer model. These embeddings are stored in a vector database (ChromaDB) to support semantic retrieval.

This allows the system to retrieve information based on meaning rather than exact keyword matching.

---

## CRAG Enhancement

After building the standard RAG pipeline, we improved it using CRAG (Corrective Retrieval-Augmented Generation).

CRAG introduces a validation step after retrieval:

- The system evaluates whether retrieved information is relevant  

- If retrieval quality is poor, it reformulates the query  

- Retrieval is performed again with improved context  

This ensures higher reliability and reduces incorrect answers.

---

## External Tools and APIs

The project uses both internal tools and external APIs.

### Internal Tools:

- Temperature converter  

- Date and time tool  

### External APIs:

- Open-Meteo API for real-time weather data  

The system also supports file ingestion from external URLs.

---

## Technologies Used

- Python  

- OpenAI API  

- Requests  

- PyMuPDF  

- BeautifulSoup  

- Sentence Transformers  

- ChromaDB
 
