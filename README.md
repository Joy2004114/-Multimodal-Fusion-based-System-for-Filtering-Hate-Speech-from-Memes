# -Multimodal-Fusion-based-System-for-Filtering-Hate-Speech-from-Memes


# 🧠 A Multimodal Fusion-based System for Filtering Hate Speech from Memes

This repository contains the official implementation of our system submitted to the **MAHED Shared Task at ArabicNLP 2025**, where our team **CUET_NLP** ranked **6th** among 42 participating teams on the final leaderboard.

---

## 📝Overview

Hateful memes in Arabic are often subtle, requiring joint reasoning over both **visual** and **textual** elements. Our proposed system combines:
- A **vision encoder** (InceptionResNetV2) for image feature extraction
- A **language encoder** (mBERT) for Arabic text embeddings
- A compact **early fusion** architecture for effective classification

 **Task:** Binary classification – Hateful vs Non-Hateful  
 **Dataset:** [QCRI Prop2Hate-Meme](https://huggingface.co/datasets/QCRI/Prop2Hate-Meme)  
 **Metric:** Macro F1-score

---

## Leaderboard Performance

| 🏅 Rank | Team        
|--------|--------------
| 1st    | NYUAD        
| 2nd    | yassirea     
| 3rd    | mzaytoon     
| 4th    | itbaan       
| 5th    | annasshaikh2003 
|**6th**    | **joy_2004114 (CUET_NLP)** 

---

## 🧩 Methodology

### 🔧 Preprocessing
- **Text**: OCR-extracted Arabic text was lowercased, cleaned, and tokenized using BERT tokenizer. Long outlier texts were filtered.
- **Image**: Resized to 128×128 pixels, normalized to `[0,1]`, and stored as NumPy arrays.

### 🧠 Feature Extraction
- **Text**: Sentence-level [CLS] embeddings from `bert-base-multilingual-cased`
- **Image**: 1536-dimensional feature vector from `InceptionResNetV2` (ImageNet weights, no top layer)

### 🔗 Fusion & Classification
- Concatenated [Text + Image] vector of size 2304
- Fully connected layers: 1024 → 512 → 256 → 128 → Softmax (2-class)
- Dropout (0.5) used to mitigate overfitting

---

## 🔍 Experiments and Results

### 🧪 Unimodal Models

| Model               | F1  | Precision | Recall | G-Mean |
|--------------------|-----|-----------|--------|--------|
| AraBERT            | 0.63| 0.61      | 0.69   | 0.64   |
| mBERT              | 0.63| 0.61      | 0.69   | 0.64   |
| BERT-base-uncased  | 0.55| 0.57      | 0.67   | 0.61   |
| InceptionNetV2     | 0.58| 0.57      | 0.60   | 0.58   |
| EfficientNetB7     | 0.48| 0.58      | 0.62   | 0.60   |

### 🤝 Multimodal Fusion Models

| Fusion Model                 | F1  | Precision | Recall | G-Mean | Official F1 |
|-----------------------------|-----|-----------|--------|--------|-------------|
| InceptionNet + AraBERT     | 0.59| 0.56      | 0.70   | 0.62   | 0.59        |
| InceptionNet + BERT        | 0.67| 0.75      | 0.61   | 0.68   | 0.60        |
| EfficientNetB7 + mBERT     | 0.67| 0.70      | 0.64   | 0.67   | 0.60        |
| EfficientNetB3 + mBERT     | 0.56| 0.60      | 0.53   | 0.55   | 0.56        |
| 🟩 **InceptionNet + mBERT** (Proposed) | **0.69** | 0.66 | 0.76 | 0.71 | **0.63** |

---

## 📁 Dataset Summary

- Total memes: ~3,000
- Hateful class: ~10% only (highly imbalanced)
- Split: 2143 train / 312 dev / 603 test  
- Source: [Prop2Hate-Meme](https://huggingface.co/datasets/QCRI/Prop2Hate-Meme)

---

## ⚙️ Hyperparameters

| Setting         | Value        |
|-----------------|--------------|
| Epochs          | 16–20        |
| Batch size      | 32           |
| Optimizer       | Adam         |
| Learning rate   | 0.001        |
| Dropout         | 0.5          |
| Max token length| 128          |

---

## 📌 Highlights

✅ Effective early fusion of mBERT and InceptionNet  
✅ Robust OCR-based text extraction pipeline  
✅ Lightweight architecture suitable for low-resource settings  
✅ Strong generalization in a highly imbalanced binary classification task  
✅ Ranked **6th** in MAHED 2025 official leaderboard

---


## 📌 Citation

If you use this code or refer to our results, please cite our paper (to be officially released in ArabicNLP 2025 proceedings):



