# Toxicity Detection with Classical and Transformer-Based Models

## Overview

This project benchmarks four models for detecting toxic comments in online text, ranging from a classical TF-IDF baseline to transformer models fine-tuned specifically on abusive language. The goal was to understand how domain-specific pretraining affects toxicity detection and whether those gains survive when models are tested on text from a completely different platform.

We trained on 159K+ Wikipedia comments across 6 toxicity categories and tested cross-domain on 10K Reddit comments. The results confirm that domain-specific pretraining helps significantly on rare toxic categories, while the classical MLP collapses entirely on Reddit because TF-IDF features cannot generalize beyond training-domain vocabulary.

## Models Compared

- **MLP** — Classical baseline using TF-IDF features and a 3-layer neural network
- **BERT** — General English transformer pretrained on Wikipedia and BookCorpus
- **BERTweet** — Transformer pretrained on 850M English tweets, adapted for social media text
- **HateBERT** — BERT further pretrained on toxic Reddit content, fine-tuned for abusive language detection

## How It Works

All four models were trained on the Jigsaw Toxic Comment Classification dataset which has 159,571 Wikipedia comments labeled across 6 categories: toxic, severe toxic, obscene, threat, insult, and identity hate. Transformer models were fine-tuned using HuggingFace Transformers and PyTorch, while the MLP used TF-IDF with TruncatedSVD for dimensionality reduction.

Cross-domain generalization was evaluated on 10,000 Reddit comments from the Real Toxicity Prompts dataset, which is a completely different platform with different vocabulary, writing style, and expression patterns than Wikipedia. This tests whether models actually learn toxicity or just memorize domain-specific patterns.

## Results

### Binary Classification — Wikipedia Validation

| Model | Accuracy | F1 | ROC-AUC |
|---|---|---|---|
| **HateBERT** | **98.95%** | **94.84%** | **99.68%** |
| BERTweet | 98.17% | 90.92% | 99.43% |
| BERT | 97.95% | 81.52% | 97.98% |
| MLP | 91.15% | 52.33% | 84.19% |

### Cross-Domain Evaluation — Reddit

| Model | Accuracy | F1 | ROC-AUC |
|---|---|---|---|
| **HateBERT** | **89.66%** | **70.86%** | **94.08%** |
| BERTweet | 88.93% | 68.22% | 93.45% |
| BERT | 88.71% | 67.62% | 93.02% |
| MLP | 74.22% | 16.52% | 49.79% |

### Domain Gap (Wikipedia → Reddit)

| Model | F1 Drop | Relative Drop |
|---|---|---|
| HateBERT | −23.98% | 25.3% |
| BERTweet | −22.70% | 24.9% |
| BERT | −13.90% | 17.0% |
| **MLP** | **−35.81%** | **68.4%** |

## Key Findings

**Domain-specific pretraining wins on rare categories**
HateBERT's pretraining on toxic Reddit content gives it the highest F1 on threat and identity hate — categories with far fewer training examples where general pretraining struggles most.

**BERTweet leads on the main toxic label**
Despite losing to HateBERT overall, BERTweet achieves the highest F1 on the main toxic label, suggesting social media pretraining better captures informal and slang-based toxicity.

**Transformer models generalize — MLP does not**
All BERT-based models maintain above 67% F1 on Reddit. MLP's ROC-AUC collapses to 0.50 — essentially random — because TF-IDF features are completely tied to training-domain vocabulary.

**Recall is the biggest failure mode cross-domain**
HateBERT's recall drops from 95% on Wikipedia to 58% on Reddit, while precision stays high. Models are over-conservative when faced with Reddit's different vocabulary and writing styles.

## Accessing the Full Code

The complete source code, training scripts, evaluation pipeline, model configurations, and visualizations are available in the private repository.

Feel free to reach out for access for interviews, collaboration, or evaluation purposes.

- **Email:** ksheerooo@gmail.com
- **LinkedIn:** [linkedin.com/in/ksheerajprakash](https://linkedin.com/in/ksheerajprakash)
🔗 GitHub Repository (private): [https://github.com/KsheerajP/Toxicity-Detector.git](https://github.com/KsheerajP/Toxicity-Detector.git)
