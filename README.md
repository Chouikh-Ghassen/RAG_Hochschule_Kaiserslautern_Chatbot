#  University AI Chat Bot -- Hochschule Kaiserslautern

An intelligent Retrieval-Augmented Generation (RAG) chatbot built to
assist students of Hochschule Kaiserslautern with questions about exams,
professors, internship requirements, and campus information.

------------------------------------------------------------------------

##  Project Overview

The University AI Chat Bot is a conversational assistant that allows
students to ask questions like:

-   "When is the next Klausur for PO19?"
-   "How do I register my Vorpraktikum?"
-   "How can I contact Professor X?"
-   "Where can I find the examination regulations?"

It uses Retrieval-Augmented Generation (RAG) to retrieve relevant
university documents and generate context-aware answers.

------------------------------------------------------------------------

## Key Features

### University Data Integration

-   Processes structured and unstructured data:
    -   Examination regulations (Klausuren)
    -   Professor contact information
    -   Internship (Vorpraktikum) guidelines
    -   Appointment schedules
    -   Semester ticket information
-   Supports: `.pdf`, `.md`, `.txt`, `.json`, `.csv`
-   Metadata tagging by document type

### Advanced Semantic Retrieval

-   Vector database powered by ChromaDB
-   Embeddings generated using OpenAI `text-embedding-3-small`
-   Natural language queries mapped to semantically relevant document
    chunks
-   Top-k retrieval (k=8) for high answer precision

### Geometric Vector Space Analysis

-   Applied t-SNE dimensionality reduction (Scikit-learn)
-   Visualized document clustering using Plotly
-   Verified semantic separation between:
    -   Professors
    -   Examination documents
    -   Internship regulations
    -   Administrative contacts

This ensures high retrieval quality and minimal hallucination.

### Conversational Intelligence

-   Built using LangChain (v0.3)
-   Conversation memory with `ConversationBufferMemory`
-   Supports follow-up questions
-   LLM: GPT-4o-mini (cost-efficient model)

### Deployment

-   Live chat interface powered by Gradio
-   Browser launch with public share link
-   Interactive conversational UI for students

------------------------------------------------------------------------

## System Architecture

    User Question
         ↓
    Gradio Chat Interface
         ↓
    ConversationalRetrievalChain (LangChain)
         ↓
    Retriever (ChromaDB)
         ↓
    Semantic Vector Search
         ↓
    Relevant Document Chunks
         ↓
    GPT-4o-mini generates contextual answer


------------------------------------------------------------------------

##  Installation & Usage (Jupyter Notebook)

Since this project is built as a **Jupyter Notebook**, you can run it
block by block.

### Clone the repository

    git clone <your-repo-url>
    cd <your-project-folder>

### Install dependencies

It is recommended to create a virtual environment:

    python -m venv venv
    source venv/bin/activate   # macOS/Linux
    venv\Scripts\activate      # Windows
    pip install -r requirements.txt

Or manually install core libraries:

    pip install langchain langchain-openai langchain-chroma chromadb openai gradio scikit-learn plotly python-dotenv

### Add your OpenAI API key

Create a `.env` file in the root directory:

    OPENAI_API_KEY=your_api_key_here

### Launch Jupyter Notebook

    jupyter notebook

Then open:

    RAG_final_version_chat_bot.ipynb

Run the notebook **cell by cell**:

-   Load and process documents\
-   Create vector database\
-   Build the retrieval chain\
-   Launch the Gradio interface
------------------------------------------------------------------------

## Dataset Statistics

-   52 total documents processed
-   173 vector chunks created
-   6 document categories
-   k=8 retrieval per query

------------------------------------------------------------------------

## Learning Outcomes

This project demonstrates:

-   Building a full RAG pipeline
-   Semantic search with vector databases
-   Document chunking strategies
-   Embedding-based retrieval evaluation
-   Conversational memory with LangChain
-   Deployment of LLM applications with Gradio
-   Vector space visualization using t-SNE

------------------------------------------------------------------------

## Future Improvements

-   Hybrid search (BM25 + semantic search)
-   Role-based access (student/admin modes)
-   Deployment via Docker
-   Migration to production-grade vector DB (e.g., Pinecone, Weaviate)
-   Multilingual support (German/English)

------------------------------------------------------------------------

## Author

Personal AI Engineering Project\
Built for Hochschule Kaiserslautern
