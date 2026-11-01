# BookWise AI — Hugging Face + FAISS RAG Chatbot

BookWise AI answers questions from uploaded PDF books and shows source passages with PDF page numbers and detected topic labels. Embeddings and answer generation use Hugging Face Inference APIs; FAISS performs vector similarity search. SQLite stores books, chunk metadata, conversations, and messages.

## Requirements
- Python 3.10+
- Hugging Face account and access token
- Internet connection for API calls and package installation

## 1. Configure Hugging Face
Create a token at https://huggingface.co/settings/tokens. Use a token with permission to call Inference Providers/models.

Copy `.env.example` to `.env` and set:
```env
HF_TOKEN=hf_your_actual_token
HF_EMBEDDING_MODEL=sentence-transformers/all-MiniLM-L6-v2
HF_CHAT_MODEL=Qwen/Qwen2.5-7B-Instruct
```
Model/provider availability can vary by account, model, and current Hugging Face Inference Provider support. If a model is not available to your token, select an embedding or chat model available through your Hugging Face Inference API.

## 2. Run on Windows PowerShell
From the extracted `BookWise-AI` folder:
```powershell
py -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
pip install -r requirements.txt
uvicorn backend.app.main:app --reload
```
If activation is blocked:
```powershell
Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
.\.venv\Scripts\Activate.ps1
```
Open http://127.0.0.1:8000

## How it works
1. PyMuPDF extracts text page by page.
2. The chunker stores each passage with its PDF page and detected topic.
3. Hugging Face Inference API generates a vector embedding for each chunk during upload.
4. Chunk vectors are stored as float32 blobs in SQLite.
5. For each question, Hugging Face embeds the query; FAISS `IndexFlatIP` ranks similar vectors.
6. The top passages are sent to the Hugging Face chat model with strict book-only instructions.
7. The UI displays answer citations and lets you open the corresponding PDF page.

## Notes
- This app uses cloud APIs; it is **not an offline chatbot**. PDF text and questions are sent to Hugging Face endpoints for inference.
- Page references are 1-based PDF page numbers, not necessarily printed book page numbers.
- Heading/topic detection is heuristic and may need refinement for some books.
- Scanned PDFs with no selectable text require OCR, which is not included in this version.
- For very large books, embedding calls are currently sent one chunk at a time. API rate limits and cost/usage limits may apply.
- Do not upload confidential PDFs unless you are comfortable sending relevant text to the configured inference provider.

## Precision answer behavior
The chat prompt instructs the Hugging Face model to answer the exact question briefly (typically 1–3 sentences) and never dump full retrieved chunks. Retrieval uses a hybrid of FAISS semantic similarity and lexical relevance to better handle short factual questions such as project names. If the chat API fails, the app reports the API issue rather than presenting a long passage as if it were an answer.
