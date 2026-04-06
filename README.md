# Weather AI Assistant
## Project Overview
This project presents an intelligent weather assistant that combines large language models, tool use, retrieval-augmented generation, corrective retrieval, and conversational memory.
The system is designed to answer different types of weather-related queries. It can retrieve real-time weather data using an external API, convert temperatures, answer date and time questions, and provide knowledge-based answers from weather-related documents.
Instead of relying on a single response method, the assistant uses an agent-based architecture to decide which tool is most appropriate for each user query.
## Main Features
The system supports the following capabilities:
- Real-time weather retrieval using the Open-Meteo API
- Temperature conversion between Celsius and Fahrenheit
- Date and time responses
- Knowledge-based question answering using RAG
- Corrective retrieval using CRAG to improve retrieval quality
## System Architecture
The project is built around an LLM-based agent.
The workflow is as follows:
1. The user submits a query
3. The LLM-based agent selects the appropriate tool
4. The selected tool is executed
5. The final response is generated for the user
The available tools are:
- weather_api
- weather_and_convert
- converter
- date_time
- rag
## Why Agentic RAG
A standard RAG pipeline is suitable only for document-based questions. However, this project includes multiple types of queries.
Some user questions require retrieval from documents, such as conceptual and explanatory questions. Other questions require real-time external data, such as current weather. Some queries require computational tools, such as temperature conversion.
For this reason, we used an agentic architecture. The agent chooses whether the system should use RAG, an API, or another tool, instead of relying only on retrieval.
## Retrieval Pipeline
The knowledge component of the project was initially built as a standard RAG pipeline.
The pipeline included the following stages:
- Loading documents from different file types
- Extracting and cleaning text
- Splitting documents into chunks
- Generating embeddings
- Storing embeddings in a vector database
- Retrieving the most relevant chunks for a given query
The document sources used in the project included:
- PDF files
- Markdown files
- HTML or web pages

## Embeddings and Vector Storage
Document chunks are converted into embeddings using a sentence-transformer model.
These embeddings are stored in a vector database to support semantic retrieval. This allows the system to retrieve text based on meaning rather than exact keyword matching.
## CRAG Enhancement
After building the standard RAG pipeline, we improved it using CRAG.
CRAG stands for Corrective Retrieval-Augmented Generation. It adds a validation step after retrieval. Instead of blindly trusting the retrieved results, the system evaluates whether the retrieved information is relevant and sufficient.
If the retrieval quality is weak, the system retries retrieval with a refined query.
This improves reliability and reduces the chance of generating answers from poor retrieval results.

## External Tools and APIs
The project uses both internal tools and external APIs.
The internal tools include:
- Temperature converter
- Date and time tool
The external API used is:
- Open-Meteo API for real-time weather data
The project also includes file reading and document ingestion from external URLs.
## Technologies Used
The project uses the following technologies and libraries:
- Python
- OpenAI API
- Requests
- PyMuPDF
- BeautifulSoup
- Sentence Transformers
- ChromaDB
