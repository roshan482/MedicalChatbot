# Medical Chatbot (RAG + LangChain + Pinecone + Gemini)

A simple medical Q&A chatbot. It indexes medical PDFs into Pinecone (vector DB), retrieves relevant chunks, and uses Google Gemini to answer questions via a Flask web UI. 

## Features
- PDF ingestion, chunking, and embedding into Pinecone for fast search. 
- RAG pipeline: retrieve top-k chunks and answer with Gemini via LangChain. 
- Minimal Flask app for chat. 

## Tech
- LangChain (retriever, chains, prompts)
- Pinecone Serverless (vector DB)
- Google Gemini (LLM via langchain-google-genai) 
- Flask (web server) 

## Setup
1) Install
pip install -r requirements.txt



2) Env vars (.env)
PINECONE_API_KEY=your_pinecone_key
GEMINI_API_KEY=your_gemini_key


3) Build index (put PDFs in data/)
python store_index.py


- Uses a 384-dim index (e.g., MiniLM). Keep index dimension matched to the embedding model.

4) Run app
python app.py


- Opens a simple chat endpoint. Ask questions based on the indexed PDFs. 

## Files
- app.py: Flask app + retriever + Gemini chat chain. 
- store_index.py: Loads PDFs, chunks text, makes embeddings, upserts to Pinecone. 
- src/helper.py: Helpers for PDFs, splitting, embeddings. 
- src/prompt.py: System/human prompts.
- templates/chat.html: Basic chat UI. 

## Notes
- Match Pinecone index dimension to your embedding model (e.g., 384 for MiniLM). 
- Provide Gemini API key via langchain-google-genai integration. 
- Tune k, chunk size, and overlap for better answers.

## Disclaimer
This is for education. It is not medical advice. Verify all outputs. 
