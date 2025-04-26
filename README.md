# Career Navigator AI

Career Navigator AI is a semantic search application that connects job descriptions and resumes using vector embeddings and Pinecone vector database. It enables intelligent matching, filtering, and exploration of resume-job relevance through a responsive Streamlit interface.

---

## Project Structure

```
CareerNavigator/
├── app.py                     # Streamlit web application entry point
├── backend/
│   ├── embedding.py            # Generate and save vector embeddings
│   ├── database.py             # Load embeddings into Pinecone index
│   └── retrieval.py            # Perform semantic search queries
├── data/
│   ├── raw/                    # (Optional) Original raw data files
│   └── processed/
│       └── embedded_data.jsonl # Embeddings after preprocessing
├── notebooks/
│   └── data_exploration.ipynb  # Jupyter Notebook for initial data analysis
├── utils/
│   └── config.py, logger.py    # (Optional) Utility and configuration files
├── .env                        # Environment variables (excluded from Git)
├── requirements.txt            # Python dependencies
└── README.md                   # Project documentation
```

---

## Key Features

- Generate text embeddings using the `all-MiniLM-L6-v2` model from Sentence Transformers.
- Store and retrieve semantic vectors using Pinecone Serverless architecture.
- Perform category-specific search: resumes, jobs, or both.
- Clean and structured UI using Streamlit with responsive design.
- Resumes displayed in field-style structured format for better readability.
- Expandable search results with collapsible containers.
- Full-text display without truncation or visual cutoff.
- Supports dark mode and light mode in Streamlit themes automatically.

---

## Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/career-navigator-ai.git
cd career-navigator-ai
```

### 2. Install Required Packages

```bash
pip install -r requirements.txt
```

### 3. Configure Environment Variables

Create a `.env` file in the root directory with the following format:

```
PINECONE_API_KEY=your_pinecone_key_here
```

### 4. Run the Application

```bash
streamlit run app.py
```

The Streamlit app will open automatically in your browser.

---

## Usage Workflow

1. **Preprocess Data**: If necessary, use `backend/embedding.py` to embed raw data and save `.jsonl` output.
2. **Upload to Pinecone**: Use `backend/database.py` to upload the embeddings into a Pinecone index.
3. **Search and Retrieve**: Use `backend/retrieval.py` for API-based semantic search.
4. **User Interface**: Operate and visualize the search results using `app.py` (Streamlit interface).

---

## Requirements

- Python >= 3.10
- streamlit
- sentence-transformers
- pinecone-client
- python-dotenv
- tqdm
- pandas
- numpy

All dependencies are listed in `requirements.txt`.

---


## Notes

- Pinecone free tier is sufficient for small-scale projects (up to 1M vectors).
- If using OpenAI for embeddings, consider API usage costs and rate limits.
- The app is designed for educational, research, and demonstration purposes.

---

## License

This project is licensed for personal, academic, and demonstration purposes only. Please contact the author if you wish to adapt it for commercial use.

