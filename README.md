# MediBot - AI-Powered Medical Chatbot

MediBot is a conversational AI chatbot built using Flask and LangChain with Google's Gemini (Generative AI) model and Pinecone for document retrieval. The bot is capable of answering medical-related queries using vector-based RAG (Retrieval-Augmented Generation).

---

## 🚀 How to Run Locally

### 🧱 Step 1: Clone the Repository

```bash
git clone https://github.com/your-username/medibot.git
cd medibot
```

### 💻 Step 2: Create a Conda Environment

```bash
conda create -n medibot python=3.10 -y
conda activate medibot
```

### 📦 Step 3: Install the Requirements

```bash
pip install -r requirements.txt
```

### 🔐 Step 4: Environment Setup

Create a `.env` file in the root directory:

```env
PINECONE_API_KEY = "your_pinecone_api_key"
GOOGLE_API_KEY = "your_google_api_key"
```

### 📚 Step 5: Store Embeddings in Pinecone

```bash
python store_index.py
```

### 🧠 Step 6: Run the Flask App

```bash
python app.py
```

### 🌐 Step 7: Open the Application

Open your browser and go to:

```
http://localhost:8080
```

---

## 🧰 Tech Stack

* **Python**
* **Flask**
* **LangChain**
* **Gemini API (Google Generative AI)**
* **Pinecone**
* **Bootstrap 4 (Frontend)**

---

## 🌍 Deploy on Render (Recommended)

**Why Render?**

* ✅ Free tier
* 🔐 HTTPS included
* 🐳 No Docker required

### 🔧 Setup Instructions

1. Create a free account at [render.com](https://render.com)
2. Connect your GitHub repo
3. Add this `.render.yaml` to your project root:

```yaml
services:
  - type: web
    name: medi-bot
    env: python
    buildCommand: pip install -r requirements.txt
    startCommand: python app.py
    envVars:
      - key: PINECONE_API_KEY
        value: your_pinecone_api_key
      - key: GOOGLE_API_KEY
        value: your_google_api_key
```

4. Deploy 🚀

---

## ✨ Final Notes

* This project uses **Gemini Pro / Flash** model from Google Generative AI.
* Built with modular structure using `LangChain`, `Flask`, and `Pinecone`.
* Frontend styled with Bootstrap for chat UI.
* For easiest deployment, use **Render**.

---

### 🔗 Project Link

📂 GitHub: [https://github.com/Lavanya294/Medical-Chatbot](https://github.com/Lavanya294/Medical-Chatbot)
