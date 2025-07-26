Bangla PDF OCR + RAG-based
Question Answering
This project extracts text from a Bengali-language PDF using OCR, cleans and normalizes the
text, breaks it into chunks, builds a vector index using semantic embeddings, and answers user
questions using a multilingual QA model with context retrieval (RAG).
---

Features
- Extracts Bengali text from scanned PDF using Tesseract OCR
- Cleans OCR errors and normalizes Bangla text
- Splits large text into meaningful, overlapping chunks
- Embeds chunks with multilingual Sentence Transformers
- Stores chunks in a FAISS vector store for fast retrieval
- Answers Bengali questions using a RAG-based QA system
---

Project Structure
bangla-pdf-ocr-rag/
│
├── data/
│ └── HSC26_Bangla_1st_paper.pdf # Your input PDF file
│
├── outputs/
│ ├── raw_text.txt # OCR output
│ ├── cleaned_text.txt # Cleaned and normalized text
│ └── faiss_index/ # Vector store
│
├── main.py # Main execution pipeline
├── requirements.txt # All required Python packages
└── README.md # This file
---
How to Run

1. Install System Dependencies (Linux)
sudo apt-get install poppler-utils tesseract-ocr tesseract-ocr-ben

2. Install Python Packages
Make sure Python 3.8+ is installed.
pip install -r requirements.txt

3. Add Your Bengali PDF
Put your PDF (e.g. textbook) into the data/ folder and rename it to match the one in main.py, or
modify the path.

4. Run the Pipeline
python main.py

This will:
Extract text from the first 60 pages of the PDF
Clean the text
Chunk it for retrieval
Create and save a FAISS vector index
Answer a sample question using RAG

Example Question
The following question is used as an example in the code:
কাকে অনুপমের ভাগ্য দেবতা বলে উল্লেখ করা হয়েছে?
If found in the PDF, the model will retrieve the relevant context and provide an accurate answer
using xlm-roberta-base-squad2.

Technologies Used
Tool/Library Purpose
pdf2image Convert PDF pages into images
pytesseract Extract Bengali text from images
transformers Load multilingual QA model
langchain Text chunking, vector store abstraction
sentence-transformers Multilingual embedding model (MiniLM)
FAISS Fast Approximate Nearest Neighbor search

Notes
The current code processes only the first 60 pages of the PDF to stay efficient. You can
increase this if needed.
Tesseract’s Bengali OCR accuracy depends on the quality of the scanned document. Post-
cleaning helps correct typical OCR errors.
The model supports both Bengali and English questions if the underlying content exists.

Author
Renu Akter Suity
