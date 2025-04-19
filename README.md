# RAG-based Personal Knowledge Assistant

A conversational AI assistant that uses Retrieval-Augmented Generation (RAG) to answer questions about your personal knowledge base, stored as markdown files.

## Overview

This project creates a personalized AI assistant that can understand and respond to questions about your personal information, projects, goals, and any other information you've stored in markdown files. It uses a combination of document retrieval techniques and Large Language Models to provide accurate, contextual responses.

## Features

- **Personalized Knowledge Base**: Uses your own markdown files as a knowledge base
- **Smart Retrieval**: Finds relevant information from your knowledge files based on semantic similarity
- **Conversational Interface**: Chat with your knowledge through an intuitive Gradio web interface
- **Source Attribution**: Responses include references to which knowledge documents were used
- **Memory**: Remembers conversation context for more natural interaction

## Requirements

- Python 3.7+
- OpenAI API key
- Google Colab (for the notebook version)
- The following Python libraries:
  - langchain
  - langchain_openai
  - faiss-cpu
  - gradio
  - transformers
  - torch

## Setup

1. Clone this repository
2. Create a folder named `Knowledge_base` with your personal markdown files
3. Set your OpenAI API key as an environment variable or in the Google Colab secrets

## File Structure

Your knowledge base should contain markdown files with your personal information. For Example:

```
Knowledge_base/
├── Personal Information.md
├── Academic Profile.md
├── Major Projects.md
├── TODOs.md
├── Friends & University Network.md
├── AI Society Two-Year Roadmap.md
├── Daily Routine.md
├── Likes & Dislikes.md
├── Goals & Dreams.md
└── ...
```

## How It Works

1. **Document Processing**: The system reads all markdown files from your knowledge base
2. **Chunking**: Long documents are split into smaller, manageable chunks
3. **Embedding**: Each chunk is converted into a vector representation using OpenAI's embedding model
4. **Storage**: Embeddings are stored in a FAISS vector database for efficient retrieval
5. **Retrieval**: When you ask a question, the system finds the most relevant chunks
6. **Generation**: The chunks and your question are sent to the LLM, which generates a response
7. **Citation**: The sources of information are added to the response

## Usage

1. Run the notebook or script
2. Wait for the knowledge base to be processed (this may take a moment)
3. When the Gradio interface appears, ask questions about your personal information
4. The assistant will provide answers based on your knowledge base

Example questions:
- "What are my main goals and dreams?"
- "Tell me about my academic background"
- "What projects am I currently working on?"
- "What is my daily routine?"

## Customization

- **Model**: Change the `MODEL` value in the `Rag` enum to use a different OpenAI model
- **Chunk Size**: Modify the `chunk_size` and `overlap` parameters in the `CharacterTextSplitter` for different chunking behavior
- **Retrieval Parameters**: Adjust the `search_kwargs` in the retriever configuration to change how many chunks are retrieved

## Future Improvements

- Add support for more file formats (PDF, Word, etc.)
- Implement document updating without reprocessing the entire knowledge base
- Add visualization of which parts of documents were used for answers
- Implement local embeddings for better privacy

## Acknowledgments

This project uses the following libraries:
- LangChain for the RAG pipeline
- FAISS for vector storage
- Gradio for the user interface
- OpenAI for embeddings and text generation
