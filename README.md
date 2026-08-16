# GenAI-Driven Stock Market Prediction

## 📌 Project Overview

Stock prices are influenced by a company's financial performance, innovations, collaborations, and overall market sentiment. News and media reports can quickly change investor perception and affect stock prices.

This project uses **Natural Language Processing (NLP), Text Embeddings, Machine Learning, Neural Networks, and Generative AI** to analyze stock-related news and provide useful insights for financial analysts.

The system performs two main tasks:

1. **Sentiment Classification** – Classifies daily stock news as Positive, Neutral, or Negative.
2. **Weekly News Summarization** – Summarizes weekly news using a pretrained **T5 Generative AI model**.

---

## 🎯 Problem Statement

An investment startup has collected historical daily news for a company listed on NASDAQ, along with daily stock prices and trading volume.

The objective is to build an AI-driven system that can:

* Analyze the sentiment of daily financial news.
* Convert news articles into meaningful numerical representations using text embeddings.
* Classify news into **Positive (1), Neutral (0), or Negative (-1)** sentiment.
* Generate weekly summaries of financial news using a Generative AI model.
* Help analysts quickly understand market sentiment and news trends.

---

## 📂 Dataset

**Dataset File:** `stock_news.csv`

| Column   | Description                                                        |
| -------- | ------------------------------------------------------------------ |
| `Date`   | Date the news was released                                         |
| `News`   | News article content                                               |
| `Open`   | Stock price at the start of the day                                |
| `High`   | Highest stock price during the day                                 |
| `Low`    | Lowest stock price during the day                                  |
| `Close`  | Adjusted stock price at the end of the day                         |
| `Volume` | Number of shares traded during the day                             |
| `Label`  | Sentiment polarity: `1` = Positive, `0` = Neutral, `-1` = Negative |

---

## 🔍 Project Approach

### 1. Data Overview & Exploratory Data Analysis

The dataset was analyzed to understand its structure and identify important patterns.

The analysis includes:

* Dataset shape
* Missing values
* Duplicate records
* Sentiment label distribution
* News text length distribution
* Stock price trends over time

### 2. Text Embeddings

Three different approaches were used to convert news text into numerical vectors:

* **Word2Vec** – Trained from scratch on the project dataset.
* **BAAI/bge-base-en-v1.5** – Pretrained Sentence Transformer embedding model.
* **all-MiniLM-L6-v2** – Pretrained Sentence Transformer embedding model.

### 3. Sentiment Classification

Each embedding technique was combined with two classification models:

* **Random Forest**
* **Neural Network using TensorFlow/Keras**

This resulted in **6 model–embedding combinations**.

The models were evaluated using:

* Accuracy
* Precision
* Recall
* F1-score

### 4. Weekly News Summarization

News articles were grouped on a weekly basis and summarized using a pretrained **T5 model**.

This provides analysts with a short and readable weekly news digest along with sentiment predictions.

---

## 📊 Model Results

| Embedding             | Model              | Test Accuracy | Test F1-Score |
| --------------------- | ------------------ | ------------: | ------------: |
| Word2Vec              | Random Forest      |         0.414 |         0.322 |
| Word2Vec              | Neural Network     |         0.443 |         0.272 |
| BAAI/bge-base-en-v1.5 | Random Forest      |         0.500 |         0.442 |
| BAAI/bge-base-en-v1.5 | Neural Network     |         0.529 |         0.521 |
| all-MiniLM-L6-v2      | Random Forest      |         0.486 |         0.409 |
| **all-MiniLM-L6-v2**  | **Neural Network** |     **0.614** |     **0.602** |

### 🏆 Best Model

The best-performing combination was:

**Sentence Transformer (`all-MiniLM-L6-v2`) + Neural Network**

* **Test Accuracy:** 61.4%
* **Test F1-Score:** 60.2%

This combination achieved the highest test accuracy and F1-score among the six evaluated combinations.

---

## 📈 Key Findings

* Random Forest models showed strong training performance but significant overfitting on the test data.
* Neural Network models showed better generalization, especially when using Sentence Transformer embeddings.
* Sentence Transformer embeddings performed better than Word2Vec in this project.
* The pretrained **all-MiniLM-L6-v2** embedding combined with a Neural Network produced the best overall test performance.
* Weekly T5 summarization provides a quick way to understand important news without reading every article individually.

---

## 💡 Recommendations

Future improvements could include:

* Fine-tuning `all-MiniLM-L6-v2` on financial and stock-market news.
* Reducing Random Forest overfitting using parameters such as `max_depth` and `min_samples_leaf`.
* Using cross-validation for better model evaluation.
* Increasing and diversifying the dataset.
* Performing further hyperparameter tuning.
* Applying Dropout and L2 regularization to the Neural Network.
* Testing additional text embedding techniques.
* Evaluating additional metrics such as ROC-AUC.
* Improving text preprocessing for emojis, slang, abbreviations, and spelling variations.
* Deploying the best model as a web application or API for real-time sentiment prediction.
* Combining weekly news summaries and sentiment predictions into an analyst dashboard.
* Periodically retraining the model with new financial news data.

---

## 🛠️ Technologies & Libraries

### Programming Language

* Python

### Machine Learning & Data Science

* NumPy
* Pandas
* Scikit-learn
* SciPy

### NLP & Text Embeddings

* Gensim
* Word2Vec
* Sentence Transformers
* `BAAI/bge-base-en-v1.5`
* `all-MiniLM-L6-v2`

### Generative AI

* Hugging Face Transformers
* T5
* PyTorch

### Deep Learning

* TensorFlow
* Keras

### Data Visualization

* Matplotlib
* Seaborn

---

## 📁 Project Structure

```text
GenAI-Driven-Stock-Market-Prediction/
│
├── Project_I_GenAI_final.ipynb
├── stock_news.csv
└── README.md
```

> **Note:** The `stock_news.csv` dataset is not included in the repository. Please refer to the dataset section for the required columns and format.

---

## ▶️ How to Run

### 1. Open the Notebook

Open `Project_I_GenAI_final.ipynb` using:

* Google Colab
* Jupyter Notebook

### 2. Add the Dataset

Place `stock_news.csv` in the path used in the **Loading the Dataset** section of the notebook.

If you are using a different location, update the dataset path accordingly.

### 3. Install Required Libraries

The project uses the following main libraries:

```bash
pip install numpy pandas scikit-learn scipy gensim sentence-transformers transformers torch matplotlib seaborn tensorflow
```

### 4. Run the Notebook

Run the notebook cells from top to bottom.

The notebook performs:

```text
Data Loading
     ↓
Data Cleaning & EDA
     ↓
Text Embeddings
     ↓
Sentiment Classification
     ↓
Model Evaluation
     ↓
Weekly News Grouping
     ↓
T5 News Summarization
```

A fixed random seed is used in model training to help make the results reproducible.

---

## 🚀 Future Scope

This project can be extended into a complete financial news analysis platform by:

* Adding real-time financial news.
* Supporting real-time sentiment prediction.
* Building an interactive Streamlit dashboard.
* Adding financial-domain-specific language models.
* Combining sentiment scores with stock-price indicators.
* Providing automated weekly market reports.
* Deploying the model through an API.

---

## 👨‍💻 Project Highlights

**Domain:** Data Analytics / Machine Learning / Generative AI

**Key Concepts:**

* NLP
* Text Embeddings
* Word2Vec
* Sentence Transformers
* Sentiment Analysis
* Neural Networks
* Random Forest
* Generative AI
* T5 Text Summarization
* Financial News Analysis

**Best Performing Model:**
`all-MiniLM-L6-v2 + Neural Network`

**Best Test Accuracy:** `61.4%`

**Best Test F1-Score:** `60.2%`
