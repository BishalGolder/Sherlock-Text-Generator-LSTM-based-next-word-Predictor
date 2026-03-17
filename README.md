#  SHerlock Text Generator

### *LSTM-Based Next Word Prediction*

---

## 📌 Problem Statement

Generating coherent and stylistically consistent text remains a challenge for many language models. While basic models can predict the next word in a sequence, they often fail to maintain narrative flow, resulting in disjointed and robotic output.

This project aims to address that limitation by training a model that not only predicts the next word but also captures the distinctive and intricate writing style of **Arthur Conan Doyle’s Sherlock Holmes** stories.

---

## 🚀 What Am I Building?

This project implements a **Neural Text Generator** using **Stacked LSTM networks** trained on Sherlock Holmes literature.

To explore architectural effectiveness, two different models were developed and compared:

* 🔁 **Bidirectional LSTM** – Processes sequences from both directions
* ➡️ **Unidirectional LSTM** – Processes sequences in a single direction

The goal is to evaluate whether bidirectional context improves stylistic coherence and narrative quality.

---

## ✨ Example Output

**Input:**

```
Sherlock Holmes was a
```

**Output:**

```
Sherlock Holmes was a very lovely...
```

---
## 📂 Repository Structure

.
├── Notebooks/
│   └── LSTM_Project_notebook.ipynb   # Main code & training pipeline
├── Models/
│   ├── Sherlock_BiLSTM.keras         # Saved Bidirectional model
│   └── Sherlock_UniLSTM.keras         # Saved Unidirectional model
├── Training_History/
│   ├── history1_bi.pkl               # Bi-LSTM training logs
│   └── history2_bi.pkl               # Uni-LSTM training logs
├── requirements.txt                  # Environment dependencies
└── README.md                         # Project documentation

---
## 📚 Dataset

* **Source:** *The Adventures of Sherlock Holmes* (Project Gutenberg)

### 🧹 Preprocessing Steps

1. Removed headers and footers, retaining only the main story content
2. Cleaned unnecessary whitespace and special characters (`\n`, `\r`, etc.)
3. Converted all text to lowercase

---

## 🧠 Approach

### 🔤 Tokenization

Used TensorFlow’s tokenizer to map each unique word to a numerical token.

### 🔗 Sequence Generation

* Context Window: 50 words (Input)
* Target Horizon: 1 word (Output)
* Mapping: Many-to-One

### 📏 Padding

Applied **pre-padding** to ensure all sequences have equal length.

---

## 🏗️ Model Architectures

### 🔹 Model 1: Bidirectional LSTM

* Embedding Layer (100-dimensional vectors)
* Bidirectional LSTM (300 neurons total)
* Unidirectional LSTM (100 neurons)
* Softmax Output Layer

---

### 🔹 Model 2: Unidirectional LSTM

* Embedding Layer
* LSTM Layer (150 neurons)
* LSTM Layer (100 neurons)
* Softmax Output Layer

---

### ⚙️ Regularization

* Dropout layers were added to both models to reduce overfitting.

---

## 🏋️ Training

* **Loss Function:** Sparse Categorical Crossentropy
* **Optimizer:** Adam
* **Epochs:** 100
* **Batch Size:** 100

### 🔄 Callbacks

* Early stopping (patience = 10 epochs)
* Learning rate reduction on plateau

---

## ✍️ Text Generation Strategy

### 🌡️ Temperature Sampling

Controls randomness in predictions:

* **Low temperature:** More deterministic, predictable text
* **High temperature:** More creative, but less coherent text

### 🎯 Top-k Sampling + Temperature

* Limits predictions to top *k* probable words
* Applies temperature scaling for balanced creativity and relevance

---

## 📊 Results & Observations

* **Bidirectional Model Accuracy:** ~42%
* **Unidirectional Model Accuracy:** ~38%

### 🔍 Key Insights

* The **bidirectional model** produced more grammatically and contextually coherent text
* It better captured sentence dependencies, especially important in Sherlock Holmes writing style
* However, it also showed **higher overfitting** compared to the unidirectional model

---

## ▶️ How to Run

1. Open the notebook in **Google Colab** (GPU recommended)
2. Change runtime to GPU
3. Run all cells
4. Save trained models and training history for later use

---

## 🔮 Future Improvements

* Incorporate **Attention Mechanisms**
* Experiment with **Transformer-based architectures**
