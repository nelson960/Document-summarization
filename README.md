# 📄 Document Summarization Pipeline

A document summarization pipeline that integrates text extraction from multiple file formats and machine learning-based text summarization using Google's Pegasus model. The workflow is structured into two main stages:

- **Data Extraction**
- **Machine Learning-Based Text Summarization**

---

## 📝 Data Extraction

The first step in the pipeline is extracting text from various document formats, including:

- **PDF** (processed with `PyPDF2`; if empty, OCR is applied using `pytesseract` and `pdf2image`)
- **DOCX** (processed using `python-docx`)
- **DOC** (processed using `antiword`, a command-line tool)
- **TXT** (handled with multiple encodings to prevent errors)
- **HTML** (parsed using `BeautifulSoup` to extract clean text and remove unnecessary tags)

The `TextExtractor` class is designed to efficiently manage text extraction from these formats.

---

## 🤖 Machine Learning-Based Text Summarization

Once the text is extracted, it undergoes preprocessing to optimize the input quality for the summarization model. This includes:

- Removing HTML tags, URLs, and excessive whitespace
- Tokenizing text into sentences using `NLTK`
- Chunking text into manageable parts to fit within Pegasus' 1024-token limit

### 🚀 Summarization Process
The pipeline leverages **Pegasus**, a state-of-the-art transformer-based sequence-to-sequence (seq2seq) model from Hugging Face's `transformers` library. It generates high-quality summaries using **beam search decoding** (`num_beams=5`).

Pegasus operates on a **PyTorch backend** and supports **GPU acceleration (MPS for Apple Silicon) or CPU fallback**.

### 🔑 Key Steps in the Summarization Pipeline
1. Extract text from different document types.
2. Preprocess the extracted text (cleaning, noise removal, and tokenization).
3. Chunk text to fit Pegasus' token limit.
4. Generate summaries using Pegasus, applying advanced NLP techniques like self-attention and transformer-based encoding-decoding.
5. Merge individual summaries to form the final condensed output.

This pipeline integrates **text extraction, NLP preprocessing, and deep learning-driven summarization**, making it a powerful tool for automated document summarization. 🚀

---

## 📚 Fine-Tuning Pegasus on CNN/DailyMail

Additionally, another notebook is included where Pegasus is fine-tuned on the **CNN/DailyMail dataset** for text summarization. The fine-tuning process covers:

- Data loading
- Preprocessing
- Tokenization
- Model training
- Evaluation

This process enhances Pegasus' ability to generate more context-aware and precise summaries.

---

## 🔧 Technologies Used
- `PyTorch`
- `transformers` (Hugging Face)
- `NLTK`
- `PyPDF2`, `pytesseract`, `pdf2image`
- `python-docx`, `antiword`
- `BeautifulSoup`

---

## 📌 Future Improvements
- Support for **multilingual document summarization**
- Integration of **BART and T5 models** for comparison
- Implementation of **Reinforcement Learning (RLHF) for better summarization refinement**

---

## 🛠️ Setup & Usage
To install the required dependencies, run:

```bash
pip install -r requirements.txt
```

To run the summarization pipeline:

```bash
python summarize.py --input_file summarize.pdf
```

For fine-tuning Pegasus, use the fine-tuning notebook provided in the repository.

---

## 📬 Contributions & Feedback
Feel free to contribute or provide feedback! Open an issue or submit a pull request if you have suggestions. 😊

