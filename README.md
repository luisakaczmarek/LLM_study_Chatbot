# LLM_study_Chatbot

## **Assignment Part 2: LLM Grader Chatbot**


This project is a Streamlit web app that evaluates student answers against reference answers using NLP techniques (TF-IDF, token overlap, sentiment, etc.).

Functionalities of the streamlit app:

1.  Loads questions and target (“standard”) answers from Q&A_db_practice.json.
2.  Shows one question at a time.
3.	Lets the user (student) type an answer.
4.	Scores it by comparing it to the reference answer using text similarity metrics (e.g., ROUGE-like F1, TF-IDF cosine).
5.	Explains differences using either rule-based text comparison or a small LLM model.
6.	Optionally analyzes user feedback sentiment (via VADER).
7.	Logs results and allows CSV download.

### **Approach followed and rationale**

To successfully design an automated system that can evaluate responses to open-ended questions in ML we created a streamlit-based chatbot that compares answers to a curated dataset of “standard” answers from the *Q&A_db_practice.json* dataset. Instead of relying on deep learning models or external APIs, we used deterministic text similarity metrics for transparent evaluation. Specifically, three complementary methods were combined:
1. Token F1 overlap (to capture exact keyword matching)
2. ROUGE-L F1 (to measure shared sequence structure and phrasing)
3. TF-IDF cosine similarity (to detect overall semantic similarity)

Each metric contributes to a weighted composite score ranging from 0 to 100, giving us a balanced assessment between lexical precision and contextual relevance. Also, we used a rule-based feedback function that highlights missing key terms and phrasing differences to justify why answers received a particular score. We also included sentiment analysis using the VADER lexicon, enabling qualitative feedback assessment, and stores all results for later analysis.

This approach prioritizes interpretability and reliability which is important for an academic grading assistant that must run consistently without GPU dependencies. However, it does not capture deeper semantic relationships or rephrased explanations as effectively as transformer-based models. To improve this, we could fine-tune or integrate a LLM such as FLAN-T5, BERTScore, or GPT-style evaluation frameworks to get contextual scoring and natural language feedback. Another improvement would be supervised learning on annotated student responses, where a regression or classification model learns to predict human-assigned scores. Also, methods like embedding-based similarity (e.g., Sentence-BERT) or semantic entailment detection could make scoring more reasonable by understanding meaning rather than surface-level similarity. To successfully do this we would need labeled data, more computational resources, and robust validation to ensure fairness and explainability.

---


## 🚀 Quick Start

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/luisakaczmarek/LLM_study_Chatbot.git
cd <your-repo>/Part2
```

---

### 2️⃣ Create and Activate a Virtual Environment

#### macOS / Linux:

```bash
python3 -m venv venv
source venv/bin/activate
```

#### Windows (PowerShell):

```powershell
python -m venv venv
venv\Scripts\activate
```

> 💡 If you see
> `zsh: permission denied: venv/bin/activate`,
> use `source venv/bin/activate` instead of running it directly.

---

### 3️⃣ Fix Dependencies (if needed)

Your `requirements.txt` already lists everything you need.
However, **remove** the line `sklearn` if it exists — it’s deprecated.

---

### 4️⃣ Install All Dependencies

```bash
pip install --upgrade pip setuptools wheel
pip install -r requirements.txt
pip install scikit-learn   # safety net, ensures availability
```

---

### 5️⃣ Run the Streamlit App

Make sure you’re in the `Part2` folder (the same one as `streamlit_app.py`):

```bash
python -m streamlit run streamlit_app.py
```

or

```bash
streamlit run streamlit_app.py
```

---

### 6️⃣ View in Browser

Once Streamlit starts, it will display:

```
Local URL: http://localhost:8501
Network URL: http://10.22.xx.xx:8501
```

Open the **Local URL** in your browser. 🎉

---

## 🧠 What the App Does

* Lets you type questions like:
  *“What is Gradient Descent?”* or *“Explain Backpropagation”*
* Fetches answers from `Q&A_db_practice.json`
* Displays them interactively using Streamlit
* Demonstrates data handling using `teachers_db_practice.csv`

---

## 🧩 Tech Stack

| Component     | Library                   |
| ------------- | ------------------------- |
| Web Framework | Streamlit                 |
| Data Handling | pandas, numpy             |
| NLP / Search  | scikit-learn, regex, nltk |
| Data Formats  | CSV, JSON                 |

---

## 🧪 Verify Installation

```bash
python -c "import streamlit, pandas, sklearn, nltk, numpy; print('✅ All good!')"
```

If you see “✅ All good!”, you’re ready to go.

---


