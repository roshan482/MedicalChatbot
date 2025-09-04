# Medical Chatbot (RAG + LangChain + Pinecone + Gemini)

A simple medical Q&A chatbot. It indexes medical PDFs into Pinecone (vector DB), retrieves relevant chunks, and uses Google Gemini to answer questions via a Flask web UI. [10][15]

## Features
- PDF ingestion, chunking, and embedding into Pinecone for fast search. [10][13]
- RAG pipeline: retrieve top-k chunks and answer with Gemini via LangChain. [10][15]
- Minimal Flask app for chat. [10]

## Tech
- LangChain (retriever, chains, prompts) [10]
- Pinecone Serverless (vector DB) [10]
- Google Gemini (LLM via langchain-google-genai) [15]
- Flask (web server) [10]

## Setup
1) Install
pip install -r requirements.txt

text
[10]

2) Env vars (.env)
PINECONE_API_KEY=your_pinecone_key
GEMINI_API_KEY=your_gemini_key

text
[15][10]

3) Build index (put PDFs in data/)
python store_index.py

text
- Uses a 384-dim index (e.g., MiniLM). Keep index dimension matched to the embedding model. [13][10]

4) Run app
python app.py

text
- Opens a simple chat endpoint. Ask questions based on the indexed PDFs. [10]

## Files
- app.py: Flask app + retriever + Gemini chat chain. [10][15]
- store_index.py: Loads PDFs, chunks text, makes embeddings, upserts to Pinecone. [10][13]
- src/helper.py: Helpers for PDFs, splitting, embeddings. [10]
- src/prompt.py: System/human prompts. [10]
- templates/chat.html: Basic chat UI. [10]

## Notes
- Match Pinecone index dimension to your embedding model (e.g., 384 for MiniLM). [13]
- Provide Gemini API key via langchain-google-genai integration. [15]
- Tune k, chunk size, and overlap for better answers. [10]

## Disclaimer
This is for education. It is not medical advice. Verify all outputs. [10]# MedicalChatbot
