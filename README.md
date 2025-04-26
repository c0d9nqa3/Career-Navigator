# Career Navigator AI

Career Navigator AI is a semantic search application that matches resumes and job descriptions using vector embeddings and a Pinecone vector database. It enables intelligent matching, filtering, and retrieval through a user-friendly Streamlit web interface.

---

## Project Structure

```
Final project/
├── backend/
│   ├── database.py             # Upload embedded vectors to Pinecone
│   ├── embedding.py            # Generate embeddings from cleaned text
│   ├── preprocessing.py        # (Optional) Data cleaning and merging
│   └── retrieval.py            # (Optional) Command-line retrieval script
├── data/
│   ├── processed/
│   │   ├── embedded_data.jsonl    # Pre-computed vector embeddings
│   │   └── merged_cleaned_dataset.csv # Cleaned dataset used for embedding
│   └── raw/
│       ├── Resume.csv             # Raw resume data
│       └── training_data.csv      # Raw job description data
├── notebooks/
│   └── data_exploration.ipynb   # Jupyter notebook for initial EDA
├── app.py                       # Streamlit web app main file
├── .env                          # API keys (excluded from GitHub)
├── .gitignore                    # Git ignore rules
└── README.md                     # Project documentation
```

---

## Setup Instructions

### 1. Clone the repository

```bash
git clone https://github.com/your-username/Career-Navigator.git
cd Career-Navigator
```

### 2. Create and activate a virtual environment

```bash
python -m venv venv
source venv/bin/activate      # On macOS/Linux
venv\Scripts\activate         # On Windows
```

### 3. Install project dependencies

```bash
pip install -r requirements.txt
```

---

## Prepare `.env` File

Create a `.env` file in the root directory with the following content:

```env
PINECONE_API_KEY=your-pinecone-api-key
```

Replace `your-pinecone-api-key` with your real Pinecone API Key.

No environment (region) variable is needed because Pinecone Serverless is used.

---

## Running Instructions

### Step 1: Data Preprocessing (Optional)

If needed, clean and merge raw data:

```bash
cd backend
python preprocessing.py
```

Output file will be saved as `data/processed/merged_cleaned_dataset.csv`.

---

### Step 2: Embedding Generation

Generate embeddings from cleaned text data:

```bash
python embedding.py
```

This will create `embedded_data.jsonl` under `data/processed/`.

---

### Step 3: Upload Embeddings to Pinecone

Upload all vectors into Pinecone index:

```bash
python database.py
```

This automatically creates the index if it does not exist.

---

### Step 4: Launch Streamlit Web App

Run the web application:

```bash
cd ..
streamlit run app.py
```

After launching, visit `http://localhost:8501` to use the search interface.

---

## Features

- Resume and job description semantic search
- Category filtering (all/resume/job)
- Top-K adjustable result retrieval
- Expandable resume details view
- Responsive and accessible UI

---

## Requirements

- Python 3.9 or 3.10
- Streamlit
- SentenceTransformers
- Pinecone-client
- Pandas
- Tqdm
- python-dotenv

(All dependencies listed in `requirements.txt`.)

---

## License

This project is licensed under the MIT License.
