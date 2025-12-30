# 🛡️ Understanding and Detecting Malicious Prompts  
### Fundamentals of Data Science (FODS)

**Author:** Mikhail Shupliakou  
**Dataset:** PL-Guard (NASK-PIB)

---

## 📖 Overview

This project explores the domain of **AI Safety**, focusing on the detection of **malicious prompts in the Polish language**.  
Using the **PL-Guard** dataset, the project investigates how machine learning and NLP models:

- represent text prompts,
- cluster safe vs. unsafe content,
- behave under adversarial attacks.

The primary goal is **not only classification**, but also an **analysis of model robustness** against adversarial techniques such as:
- text obfuscation,
- leetspeak,
- injected noise and typos.

---

## 🚀 Key Features & Methodology

The project pipeline consists of the following stages:

### 1️⃣ Text Representation (Embeddings)
- Used **BERT** to encode Polish text prompts into **768-dimensional embeddings**.

### 2️⃣ Dimensionality Reduction
- Applied **PCA**, **t-SNE**, and **UMAP** to:
  - visualize the embedding space,
  - analyze separability between safe and unsafe prompts.

### 3️⃣ Clustering Analysis
- Evaluated:
  - **K-Means**
  - **Agglomerative Clustering**
  - **DBSCAN**

**Finding:**  
Pre-trained embeddings cluster mainly by **topic** (e.g. finance, cooking) rather than **safety intent**, indicating the need for **fine-tuning** in moderation tasks.

### 4️⃣ Outlier Detection
- Implemented **distance-based anomaly detection**.
- Adversarial prompts often appear as **outliers** in embedding space.

### 5️⃣ Classification & Robustness Testing
- Trained classical ML models:
  - Logistic Regression
  - Support Vector Machine (SVM)
  - Random Forest

**Baseline accuracy:** ~74–80% on clean data.

- Tested models on **adversarial examples**  
  → Accuracy dropped to **~22%**, revealing severe brittleness.

### 6️⃣ Defense Strategy
- Applied **Adversarial Training**.
- Restored robustness to **~76% accuracy** on attacked data.

---

## 📂 Project Structure

```plaintext
FODS_Project/
├── fods_project.ipynb        # Main Jupyter Notebook (code + analysis)
├── report/
│   └── main.pdf              # Final project report
├── .gitignore                # Ignored files
├── README.md                 # Project documentation
└── requirements.txt          # Python dependencies
