# SemEval-2025 Task 11 Track B: Emotion Intensity Detection

This repository contains the official submission  to **SemEval-2025 Task 11: Track B — Emotion Intensity Detection**. The task involves predicting the intensity of six primary emotions — *anger, disgust, fear, joy, sadness, and surprise* — on a 0–3 ordinal scale across 11 languages.

📄 **Paper**: [SemEval‑2025 Task 11 Overview Paper (Muhammad et al.)](https://arxiv.org/abs/2503.07269)  
👨‍💻 **Authors**: Joseph Khanh Le, Hannah Cui, James Zhang (Stanford University)

---

## 🚀 Overview

We fine-tuned a multilingual BERT-based regression model to predict emotion intensity from short text snippets across the following 11 languages:

- Amharic
- Algerian Arabic
- Mandarin Chinese
- German
- English
- Spanish
- Hausa
- Portuguese
- Romanian
- Russian
- Ukrainian

Our system leveraged:
- **HuggingFace Transformers** (`bert-base-uncased`)
- **PyTorch** for modeling and training
- **Regression loss (MSE)** for fine-grained prediction
- **Early stopping**, **ExponentialLR scheduling**, and **AdamW optimization**

---

## 🧠 Model Architecture

- **Base Model**: BERT (bert-base-uncased)
- **Task Type**: Regression (`AutoModelForSequenceClassification`, `num_labels=1`)
- **Loss Function**: Mean Squared Error (MSE)
- **Optimizer**: AdamW
- **Scheduler**: ExponentialLR (γ = 0.99)
- **Training**: 15 epochs, early stopping after 3 stagnant epochs
- **Evaluation**: Predictions rounded to nearest integer in [0, 3]; considered accurate if deviation < 0.5

---

## 📊 Performance

- **Validation Accuracy**: 68.97% (defined by ±0.5 margin)
- **Validation Loss**: 0.373 MSE
- Strong performance on **high-resource** languages (English, Spanish)
- Lower performance on **low-resource** languages (e.g., Hausa, Amharic)

---

## 🔍 Key Lessons & Limitations

- Multilingual training helped with high-resource languages but struggled on low-resource data
- Model had difficulty distinguishing **moderate vs. strong** emotions
- Co-occurrence of multiple emotions led to false positives/negatives
- Future directions include:
  - Ensemble learning
  - Emotion-aware embeddings
  - Contrastive learning techniques
  - Using RoBERTa / DeBERTa architectures

---

## 📜 Citation

If you use this code or build upon it, please cite:

```
Muhammad, S. H., et al. (2025). SemEval‑2025 Task 11: Bridging the Gap in Text-Based Emotion Detection. In *Proceedings of the 19th International Workshop on Semantic Evaluation (SemEval-2025)*. Association for Computational Linguistics. https://arxiv.org/abs/2503.07269
```

---

## 🧠 Contact

For questions or collaboration:  
📧 josephle@stanford.edu  
