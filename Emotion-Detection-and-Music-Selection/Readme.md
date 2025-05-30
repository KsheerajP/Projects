# AI-Based Emotion Detection and Music Selection System

## Overview
This project implements a multi-modal emotion recognition system that analyzes user inputs from facial expressions, voice signals, and text to determine emotional state and suggests music accordingly. It aims to enhance user well-being and personalization in music playback using deep learning and psychological emotion-music mapping models.

---

## Features
- Facial Emotion Detection using **DeepFace CNN** for expression analysis.
- Voice Emotion Classification using **MFCC feature extraction** and traditional ML classifiers.
- Text Sentiment Analysis using **VADER**, **NLTK**, and keyword-based mapping.
- Mood-to-Music mapping using **Valence-Arousal models** and genre-based matching.
- Real-time emotion sensing with **offline-compatible playback interface**.

---

## Dataset
This system uses a combination of public datasets:
- **FER2013** for facial emotion classification.
- **RAVDESS** and **CREMA-D** for voice emotion recognition.
- Custom-labeled text sentiment samples for training the NLP model.

---

## Results
- Achieved maximum accuracy of **88%** across facial, voice, and text detection modules.
- F1-score of **0.85** across the multi-modal classifier.
- User testing showed high relevance of music suggestions to perceived emotional state.

---

## How to Run
1. Clone the repository and install the dependencies:
```bash
pip install -r requirements.txt
