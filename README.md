# ✈️ GenAI Airline Review RAG Pipeline

This project implements a **cloud-based GenAI-powered data pipeline** using [Langflow](https://www.langflow.org/) on **Datastax AI Platform (PaaS)** with **AstraDB vector storage**. The system enables Retrieval-Augmented Generation (RAG) over real airline review data to answer user queries like:


## ✅ Project Features

- Ingests unstructured airline review data (CSV or PDF)
- Splits and vectorizes review content using OpenAI Embeddings
- Stores embedded data in AstraDB vector-enabled collections
- Accepts natural language queries via Langflow UI
- Retrieves and injects context into LLM (gpt-4o or gpt-3.5)
- Deployed fully within **Datastax AI PaaS** (Langflow inside Astra Studio)

---

## 📂 Included Files

| File | Purpose |
|------|---------|
| `airline_review_rag.json` | Working RAG pipeline (live, ready for query) |
| `airline_review_ingestion.json` | Optional ingestion flow + RAG (open in separate project) |
| `airline_reviews_5k.csv` | Cleaned review dataset |
| `airline_reviews_unstructured.pdf` | Unstructured version for ingestion |

---

## 🔍 RAG Workflow Overview

The **retrieval flow** uses:
- `Input` → `Embedding` → `AstraDB VectorStore` → `Prompt` → `OpenAI LLM` → `Output`

All queries run against a pre-loaded AstraDB collection called `airline_review_rag`.

Example queries:
- “Which airline's have good economy seat reviews for flights from New York??”
- “Which airlines have poor seat comfort in economy according to reviews?”
- “Which airlines are delayed most often according to reviews?”

---

## 🧾 Data Ingestion

I decided to manually ingest data via file upload in AstraDB in order to test vector search. So, although the data was originally uploaded manually into AstraDB using the **Upload Data UI**, a Langflow-native ingestion flow is also included for demonstration. This also includes the original RAG flow for your convenience, just make sure to open it in a separate project.

The `airline_review_ingestion.json` flow shows how you could:
1. Upload a file (`.csv` or `.pdf`)
2. Chunk the text into 800-character segments
3. Embed using OpenAI
4. Store in AstraDB

### 🔐 Note:
Langflow does **not persist tokens or API keys**, so after importing the flow, you must:
- Paste your **AstraDB Token**
- Add your **API Endpoint**
- Set your **OpenAI API Key**
- Create your own **database**
- Create your own **collection**

---

## 🚀 How to Run This Project

1. Create a free [Datastax AstraDB](https://www.datastax.com/astra) account
2. Create a **vector-enabled** database
3. Generate an **application token** (Admin role)
4. [Open Langflow](https://www.langflow.org) or use Langflow inside Astra Studio
5. Import `airline_review_retrieval.json`
6. Paste in your AstraDB credentials
7. Click “Playground” and try sample queries!

📝 *To ingest the dataset, import `airline_review_ingestion.json` and use `airline_reviews_unstructured.pdf` as input or like i did it, manually setup AstraDB database and collection and upload `airline_reviews_unstructured.pdf`. so you can test out vector search.*

---

## 👨‍🏫 Notes for Reviewers / Instructors

- The retrieval flow is fully functional and connected to real embedded review data
- The ingestion flow is only illustrative and included to demonstrate pipeline design — would recommend setting up collection via upload in AstraDB
- Credentials must be re-entered due to Langflow’s secure environment

---


## 🙌 Acknowledgements

- Dataset: [Kaggle Airline Review Dataset] (https://www.kaggle.com/datasets/juhibhojani/airline-reviews)
- Tools: Langflow, AstraDB, OpenAI, Datastax AI Studio

