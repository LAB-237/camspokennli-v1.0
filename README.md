# CamSpokenNLI v1.0

Official repository for **CamSpokenNLI v1.0**, a pilot spoken Natural Language Inference (NLI) dataset and baseline evaluation framework designed for low-resource, code-mixed African linguistic varieties - specifically **Cameroon Pidgin English** and **Camfranglais**.

---

## 📌 Overview

Natural Language Inference and spoken processing tasks are heavily underrepresented in regional African vernaculars. **CamSpokenNLI v1.0** addresses this data vacuum by providing a structured resource pairing spoken audio files with text transcripts, English glosses, and inference labels. This repository houses the code, preprocessing pipelines, stratified fold splitting, and evaluation harnesses used to benchmark small language models (SLMs) and speech-to-text models.

---

## 📂 Repository Structure

```text
├── preprocessing/      # Audio normalization, 16kHz resampling, and silence trimming scripts
├── evaluation/         # NLI cross-validation loops, transfer matrices, and binomial test harnesses
├── notebooks/          # Complete Colab rerun notebook (CamSpokenNLI_v1_COMPLETE_corrected_rerun.ipynb)
├── results/            # Exported CSV matrices, per-seed statistics, and transcripts
└── requirements.txt    # Python dependencies (transformers, datasets, whisper, torch, etc.)
```
---

# ⚙️ Hardware & Experimental Specifications

To ensure exact reproducibility, all baseline experiments are configured around the following parameters (matching Appendix A of the paper):

* **Hardware Environment:** Single NVIDIA Tesla T4 GPU via Google Colab.
* **Base Model:** xlm-roberta-base with a three-way classification head.
* **Input Representation:** Premise and hypothesis formatted as a sentence pair (premise-only and hypothesis-only baselines use single sides).
* **Hyperparameters:**
  * **Learning Rate:** 2 × 10⁻⁵ (linear schedule)
  * **Batch Size:** 4 per-device train, 8 per-device eval
  * **Epochs:** 15 for main experiments; 5 and 10 for sensitivity studies
  * **Optimizer / Weight Decay:** AdamW with weight decay set to 0.0
  * **Maximum Sequence Length:** 64 tokens
* **Evaluation Protocol:**
  * **Random Seeds:** 42, 123, 2024 (three repeated runs per condition, reporting mean and sample standard deviation)
  * **Folds:** 5 stratified item-level folds sharing a single fold assignment 2 × 10⁻⁵ across both varieties and all model seeds
  * **Cross-Variety Transfer:** Disjoint-item splits ensuring source-variety training items and target-variety test items never overlap

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
### 3. Execution & Reproduction (Google Colab Pipeline)
The experimental pipeline is organized into five modular phases to ensure reproducibility, transparency, and seamless recovery from runtime disconnections[cite: 6]:

* **Phase A - Data Ingestion & Validation:** Validates CSV schemas (UTF-8 with BOM, 114 rows per variety) and converts raw audio into 16 kHz mono WAV format with conservative energy trimming.
* **Phase B - Shared Stratified Folds:** Establishes a single fixed item-level **5-fold split seed = 42** shared uniformly across all models and transfer directions.
* **Phase C - NLI Fine-Tuning & Sweep:** Trains `xlm-roberta-base` across native text, English-gloss references, disjoint cross-variety transfer, and an expanded epoch sensitivity horizon **(5, 10, and 15 epochs)** over model seeds `[42, 123, 2024]`.
* **Phase D - Whisper ASR Diagnostics:** Evaluates zero-shot automatic speech recognition (Base, Small, Large-v3) using automatic language identification and forced-language diagnostics.
* **Phase E - Artifact Export & Manifests:** Compiles final Table 1/2 matrices, granular Appendix audit records, and comprehensive run manifests directly to Google Drive.
---

## 🤗 Datasets & Ecosystem

The raw audio files, metadata, and official dataset cards are hosted openly on Hugging Face:
* **Dataset Hub:** [Hugging Face - LAB-237](https://huggingface.co/lab237)
* **Organization Hub:** [GitHub - LAB-237](https://github.com/lab-237)

---

## ⚖️ License

Published under the **Apache License 2.0**. See the `LICENSE` file for details.

---
*Maintained by the **LAB-237***
