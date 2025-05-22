# Vietnamese-Lao Machine Translation using Transformer

This project implements a machine translation system between Vietnamese and Lao languages using the Transformer architecture — built from scratch without using any pre-trained models. It was developed as a final project for the Natural Language Processing course (INT3406 1) at UET.

## 🧠 Overview

- **Task**: Build a bidirectional translation model for Vietnamese ↔ Lao.
- **Architecture**: Transformer (Vaswani et al., 2017), implemented with PyTorch.
- **No pre-trained models or libraries were used** — all components including attention, encoder, decoder, and positional encoding were implemented manually.
- **Evaluation Metrics**: SacreBLEU and inference speed.

## 📂 Dataset

Provided by VLSP2023 (Vietnamese Language and Speech Processing):

- **Training set**: 100,000 sentence pairs per language.
- **Validation set**: 2,000 sentence pairs.
- **Test set**:
  - Public: 100,000 sentence pairs.
  - Private: 2,000 sentence pairs for each translation direction (Vi→Lo, Lo→Vi).

### 🔍 Notes

- SentencePiece was used for separate tokenization (BPE) for both languages.
- Due to the lack of high-quality external data, only the provided VLSP2023 data was used.

## ⚙️ Model Details

### Tokenization
- Trained BPE tokenizers using SentencePiece for both languages.
- Tokenized data saved in `.csv` format for reuse.

### Transformer Architecture
- Built from the ground up:
  - Encoder: 6 layers with Multi-Head Self-Attention and Feedforward layers.
  - Decoder: 6 layers with Masked Self-Attention and Encoder-Decoder Attention.
  - Positional Encoding: Rotary Positional Encoding was used.
  - Attention mechanisms implemented based on "Attention is All You Need".

### Training
- Loss function: Cross-entropy
- Optimizer: Adam with learning rate scheduler
- Gradient clipping applied
- Batch size: 32, padded up to max 128 tokens
- Models saved based on lowest validation loss

## 📈 Results

| Direction   | BLEU (Public) | BLEU (Private) | Inference Time | Tokens/sec |
|-------------|---------------|----------------|----------------|------------|
| Vi → Lo     | 24.81         | 24.81          | 236.69s        | 500.02     |
| Lo → Vi     | 18.58         | 0.00           | 275.89s        | 498.79     |

> ⚠️ BLEU = 0 in Lo→Vi private test suggests possible evaluation errors.

## 👨‍💻 Contributors

- **Hoàng Duy Anh** — coding & report  
- **Nguyễn Khôi Nguyên** — coding & model training  
- **Nguyễn Trần Phương Hà** — report & presentation

## 📚 Reference

- Vaswani et al., *Attention is All You Need*, 2017

---

> 🔎 *This project demonstrates the feasibility of low-resource translation without leveraging external pre-trained models, but results suggest further optimization and data refinement are needed for better performance.*

