# RAG LLM — Document Question Answering System

A Retrieval-Augmented Generation (RAG) application that allows users to upload documents and ask questions about their contents.

The system retrieves relevant information from the uploaded documents and uses an LLM to generate answers based **only on the provided document content**.

## Features

* Upload and process documents
* Extract text from documents
* Split documents into smaller chunks
* Generate vector embeddings
* Store and search document embeddings
* Retrieve relevant document sections for each question
* Generate answers using an LLM
* Answers are grounded in the uploaded documents
* Web-based interface for interacting with the system
* Environment variables used for API keys and configuration

## How It Works

The application follows a Retrieval-Augmented Generation pipeline:

```text
Document
   ↓
Text Extraction
   ↓
Text Chunking
   ↓
Embeddings
   ↓
Vector Database
   ↓
User Question
   ↓
Similarity Search
   ↓
Relevant Document Chunks
   ↓
LLM
   ↓
Answer
```

Instead of sending the entire document to the LLM for every question, the system first retrieves the most relevant sections and provides those sections as context to the model.

## Tech Stack

* **Python**
* **Flask**
* **OpenAI API**
* **LangChain**
* **ChromaDB**
* **HTML / CSS / JavaScript**
* **Python-dotenv**

## Project Structure

```text
RAG-LLM/
│
├── app.py
├── requirements.txt
├── .env.example
├── .gitignore
├── README.md
│
├── templates/
│   └── ...
│
├── static/
│   ├── css/
│   └── js/
│
├── services/
│   └── ...
│
├── utils/
│   └── ...
│
└── knowledge-base/
    └── ...
```

## Installation

### 1. Clone the repository

```bash
git clone https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git
cd YOUR_REPOSITORY
```

### 2. Create a virtual environment

Windows:

```bash
python -m venv venv
```

Activate it:

```bash
venv\Scripts\activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure environment variables

Create a `.env` file:

```env
OPENAI_API_KEY=your_api_key_here
```

Do **not** commit your `.env` file.

A `.env.example` file is provided as a template.

### 5. Run the application

```bash
python app.py
```

Then open the local URL shown by Flask in your browser.

## Example Use Case

A user uploads a document containing information about a particular topic.

They can then ask:

```text
What are the main objectives discussed in the document?
```

The RAG pipeline retrieves the relevant sections and provides them to the LLM as context.

The system then generates an answer based on that context rather than relying solely on the model's general knowledge.

## RAG Pipeline

### 1. Document Loading

The application reads the uploaded document and extracts its text.

### 2. Text Splitting

Large documents are divided into smaller chunks so that relevant sections can be efficiently retrieved.

### 3. Embedding Generation

Each chunk is converted into a vector representation using an embedding model.

### 4. Vector Storage

The embeddings are stored in a vector database for efficient similarity searching.

### 5. Retrieval

When the user asks a question, the question is converted into an embedding and compared with the stored document embeddings.

The most relevant chunks are retrieved.

### 6. Generation

The retrieved chunks are provided to the LLM as context.

The LLM generates the final answer using the retrieved information.

## Important Design Principle

The purpose of this application is to provide **document-grounded answers**.

The model should use the retrieved document content as its primary source of information and avoid introducing unrelated information that is not supported by the uploaded documents.

## Environment Variables

The application uses environment variables for sensitive configuration.

Example:

```env
OPENAI_API_KEY=
```

The actual `.env` file is excluded from Git using `.gitignore`.

## Future Improvements

* Support additional document formats
* Add document citations to answers
* Improve retrieval accuracy
* Add conversation history
* Support multiple documents simultaneously
* Add document management
* Add retrieval evaluation metrics
* Add authentication
* Improve frontend UI

## License

This project is intended for educational and portfolio purposes.
