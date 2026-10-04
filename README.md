# CamSpokenNLI v1.0

Official repository for **CamSpokenNLI v1.0**, a pilot spoken Natural Language Inference (NLI) dataset and baseline evaluation framework designed for low-resource, code-mixed African linguistic varieties - specifically **Cameroon Pidgin English** and **Camfranglais**.

---

## 📌 Overview

Natural Language Inference tasks are heavily underrepresented in regional African vernaculars. **CamSpokenNLI v1.0** addresses this data vacuum by providing a structured resource pairing spoken audio files with text transcripts and inference labels. This repository houses the code, preprocessing pipelines, and evaluation harnesses used to benchmark small language models (SLMs) and speech-to-text models.

---

## 📂 Repository Structure

```text
├── preprocessing/      # Audio normalization, text cleaning, and dialectal formatting scripts
├── evaluation/         # Evaluation loops, baseline test frames, and accuracy metrics
└── requirements.txt    # Python dependencies (transformers, datasets, torchaudio, etc.)
```
---

## 🚀 Getting Started

### 1. Clone the Repository
```bash
git clone https://github.com/cameroon-ai-lab/camspookennli-v1.0.git
cd camspookennli-v1.0
```

### 2. Install Dependencies
```bash
pip install -r requirements.txt
```

---

## 🤗 Datasets & Ecosystem

The raw audio files, metadata, and official dataset cards are hosted openly on Hugging Face:
* **Dataset Hub:** [Hugging Face - Cameroon AI Research Lab](https://huggingface.co/cameroon-ai-lab)
* **Organization Hub:** [GitHub - Cameroon AI Research Lab](https://github.com/cameroon-ai-lab)

---

## ⚖️ License

Published under the **Apache License 2.0**. See the `LICENSE` file for details.

---
*Maintained by the **Cameroon AI Research Lab** | Department of Computer Engineering, University of Buea, Cameroon*
