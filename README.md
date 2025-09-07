# document_Question_Answers
This model uses take's pdf as an input and allow user to ask query and answer then using Gemini .
Chat with your PDF using Google Gemini
This project is a web application built with Streamlit that allows you to upload a PDF document and ask questions about its content. The application utilizes Google's Gemini Pro model through the LangChain framework to understand the document and provide answers.

Features
Upload PDF Files: Easily upload any PDF document directly in the web interface.

Ask Questions: Interact with your document by asking questions in natural language.

Conversational Memory: The chatbot remembers the context of the conversation.

Powered by Gemini: Leverages the power of Google's state-of-the-art gemini-1.5-flash-latest model for question answering and models/embedding-001 for text embeddings.

How It Works
PDF Processing: When a PDF is uploaded, the application extracts the text from its pages.

Text Chunking: The extracted text is split into smaller, manageable chunks.

Embedding Generation: Google's Generative AI model creates vector embeddings for each text chunk.

Vector Store: The embeddings are stored in a Chroma vector database for efficient retrieval.

Question Answering: When you ask a question, the application creates an embedding for the query and retrieves the most relevant text chunks from the vector store.

Response Generation: The retrieved chunks and the conversation history are passed to the Gemini chat model, which then generates a relevant answer.

Setup and Installation
To run this application locally, you'll need to install the required Python libraries.

Clone the repository:

git clone <your-repository-url>
cd <your-repository-name>

Install dependencies:

pip install streamlit chromadb langchain langchain-community pypdf langchain-google-genai google-generativeai

Set up your Google API Key:
You need a Google API key to use the Gemini models. Set it as an environment variable:

export GOOGLE_API_KEY="YOUR_API_KEY_HERE"

Alternatively, you can modify the app.py file to directly include your key, but using environment variables is recommended for security.

How to Run the Application
Once the setup is complete, you can run the Streamlit application with the following command:

streamlit run app.py

This will start the web server and open the application in your default web browser.

Code Overview
The main logic is contained within app.py:

UI: Built using Streamlit for file uploading, text input, and displaying the conversation.

PDF Handling: pypdf is used to read and extract text from the uploaded PDF.

Text Splitting: langchain.text_splitter.CharacterTextSplitter is used to break the document text into chunks.

Embeddings: langchain_google_genai.GoogleGenerativeAIEmbeddings generates embeddings using the "models/embedding-001" model.

Vector Store: langchain_community.vectorstores.Chroma creates an in-memory vector database.

LLM: langchain_google_genai.ChatGoogleGenerativeAI provides the interface to the Gemini chat model.

Conversational Chain: langchain.chains.ConversationalRetrievalChain manages the retrieval from the vector store and the conversation flow.
