# 📱 End-To-End SMS Spam Detector

> An NLP-powered web application that classifies SMS messages as **Ham ✉️** or **Spam 🚫** in real time — built with Machine Learning and deployed on Streamlit.

<p align="center">
  <a href="https://spam-detector-talvr2jjfrfmuazwchjebm.streamlit.app/">
    <img src="https://img.shields.io/badge/🚀 Live Demo-Streamlit-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white" alt="Live Demo"/>
  </a>
  <img src="https://img.shields.io/badge/Python-3.9+-3776AB?style=for-the-badge&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikitlearn&logoColor=white"/>
  <img src="https://img.shields.io/badge/NLP-NLTK-009900?style=for-the-badge"/>
</p>

---

## 🔗 Live Demo

> 🌐 **Try the app here:** [https://spam-detector-talvr2jjfrfmuazwchjebm.streamlit.app/]

---

## 📌 Table of Contents

- [Overview](#overview)
- [Demo Preview](#demo-preview)
- [Dataset](#dataset)
- [NLP Pipeline](#nlp-pipeline)
- [Models Compared](#models-compared)
- [Results](#results)
- [Project Structure](#project-structure)
- [How to Run Locally](#how-to-run-locally)
- [Tech Stack](#tech-stack)

---

## 🔍 Overview

This project was built as a college NLP assignment. It takes an SMS message as input and predicts whether it is:

| Label | Meaning |
|-------|---------|
| ✉️ **Ham** | A legitimate message |
| 🚫 **Spam** | An unwanted/malicious message |

The full pipeline covers data cleaning, exploratory data analysis, text preprocessing, TF-IDF vectorization, class imbalance handling with SMOTE, training and comparing 10 classifiers, and final deployment via Streamlit.

---

## 🖥️ Demo Preview

> Screenshot of the app making a live prediction:

![App Prediction Screenshot](https://raw.githubusercontent.com/Mohanad06/Spam-Detector/main/screenshots/Prediction.PNG)

---

## 📂 Dataset

**UCI SMS Spam Collection Dataset** — a widely used NLP benchmark.

| Property | Value |
|----------|-------|
| Total messages | 5,572 |
| Ham messages | ~4,825 (~87%) |
| Spam messages | ~747 (~13%) |
| Source | [Kaggle](https://www.kaggle.com/datasets/uciml/sms-spam-collection-dataset) |

> ⚠️ The dataset is **imbalanced** (13% spam). This is handled using **SMOTE** applied exclusively on the training set.

---

## ⚙️ NLP Pipeline

| Step | Technique |
|------|-----------|
| 1️⃣ Data Cleaning | Drop empty columns, rename, remove duplicates |
| 2️⃣ Label Encoding | `ham → 0`, `spam → 1` |
| 3️⃣ EDA | Distribution plots, word clouds, correlation heatmap |
| 4️⃣ Text Preprocessing | Lowercase → Tokenize → Remove stopwords/punctuation → Porter Stemming |
| 5️⃣ Vectorization | TF-IDF (max 3,000 features) |
| 6️⃣ Class Balancing | SMOTE on training set only |
| 7️⃣ Model Training | 10 classifiers trained and compared |
| 8️⃣ Serialization | `vectorizer.pkl` + `model.pkl` via Pickle |

---

## 🤖 Models Compared

10 classifiers were trained and evaluated. The primary metric is **Precision** — in spam detection, falsely flagging a legitimate message as spam is more costly than missing a spam.

| Classifier | Notes |
|-----------|-------|
| BernoulliNB ✅ | **Final model** — highest precision |
| MultinomialNB | Strong baseline for text |
| SVM (Sigmoid) | Competitive but slower |
| Logistic Regression | Good precision/recall balance |
| Random Forest | High accuracy, slightly lower precision |
| Extra Trees | Similar to RF |
| Gradient Boosting | Slower, comparable performance |
| AdaBoost | Moderate results |
| Bagging | Ensemble baseline |
| KNN | Weakest on sparse TF-IDF features |

> 🏆 **BernoulliNB** was selected as the final model — it consistently delivered the highest precision while keeping false positives (ham flagged as spam) at a minimum.

---

## 📊 Results

| Metric | Score |
|--------|-------|
| Accuracy | ~97% |
| Precision (Spam) | ~100% (on test set) |

The final model produces very few false positives — legitimate messages are almost never incorrectly flagged as spam.

---

## 📁 Project Structure

```
sms-spam-detector/
│
├── app.py                               # Streamlit web application
├── requirements.txt                     # Python dependencies
│
├── model.pkl                            # Trained BernoulliNB model
├── vectorizer.pkl                       # Fitted TF-IDF vectorizer
│
├── spam.csv                             # Raw dataset (UCI SMS Spam Collection)
│
├── End-To-End_SMS_Spam_Detector.ipynb   # Full training notebook
│
└── screenshots/
    └── prediction.png                   # App screenshot (for README)
```

---

## ▶️ How to Run Locally

### Prerequisites
- Python 3.9 or higher — [Download here](https://www.python.org/downloads/)

### Steps

```bash
# 1. Clone the repository
git clone https://github.com/Mohanad06/Spam-Detector.git
cd Spam-Detector

# 2. Install dependencies
pip install -r requirements.txt

# 3. Run the Streamlit app
streamlit run app.py
```

The app will open automatically in your browser at **http://localhost:8501**

### Using the App

1. Type or paste any SMS message into the text box
2. Click **Predict**
3. The model will instantly classify it as **Ham ✉️** or **Spam 🚫**

---

## 🧰 Tech Stack

| Component | Technology |
|-----------|-----------|
| Language | Python 3.9+ |
| NLP | NLTK (tokenization, stopwords, stemming) |
| Vectorization | scikit-learn TF-IDF |
| Imbalance Handling | imbalanced-learn (SMOTE) |
| ML Models | scikit-learn |
| Final Model | BernoulliNB |
| Deployment | Streamlit |
| Serialization | Pickle |
| Visualization | Matplotlib, Seaborn, WordCloud |

---

## 👤 Author

- **Name:** Mohanad Mostafa  
- **College:** BFCAI  
- **Course:** Natural Language Processing
---

## 📄 License

This project is for educational purposes only.
