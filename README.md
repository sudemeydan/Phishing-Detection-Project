# LLM-Assisted Phishing Email Detection System

---

## Overview

This project presents a deep learning–based phishing email detection system that leverages **contextual language understanding** and **Large Language Model (LLM)–assisted explainability**. The system combines a Transformer-based text encoder (**XLM-RoBERTa**) with a reasoning-oriented LLM (**Mistral**) to detect phishing emails and generate human-readable explanations for its predictions.

Unlike traditional rule-based or classical machine learning approaches, this system focuses on **semantic manipulation, contextual inconsistencies, and social engineering patterns** commonly used in modern phishing attacks.

---

## Key Features

- Binary classification: **Phishing vs. Legitimate**
- Multi-class phishing category prediction:
  - Finance
  - Account
  - Shopping
  - Service
  - Organization
  - Prize
- Contextual text representation using **XLM-RoBERTa**
- Class imbalance handling with stratified splitting and class-weighted loss
- LLM-powered explainability using **Mistral**
- Natural language explanations based on linguistic and technical indicators
- Designed for real-time analysis and web deployment

---

## Dataset Creation and Enrichment

### Dataset Construction

The dataset was constructed through a **multi-stage data collection and preprocessing pipeline** designed to accurately reflect real-world phishing email scenarios. Instead of relying on a single static source, multiple datasets and external resources were combined to improve robustness and diversity.

Publicly available email datasets obtained from the **Figshare platform** were used as the initial data source. These raw datasets contained structural inconsistencies, where email subjects, message bodies, URLs, and numerical prefixes were often mixed together. A comprehensive cleaning process was applied to separate subject and body fields, remove corrupted or empty samples, and eliminate formatting noise.

---

### Data Enrichment

To capture modern and sophisticated phishing attack patterns, the dataset was iteratively enriched using external phishing intelligence sources. **Up-to-date phishing URLs** were collected from the **PhishTank database** and integrated into the dataset. Additionally, a custom web scraping mechanism was employed to gather both legitimate and malicious URL structures observed in real-world environments.

This enrichment strategy enabled the dataset to include:

- Simple phishing emails
- Advanced social engineering attacks
- Boundary-case phishing examples
- Legitimate emails with and without URLs

---

### Phishing Category Labeling

Beyond binary classification, phishing emails were categorized to support **multi-class classification**. An automated keyword-based labeling approach was applied using frequency and contextual analysis over email subjects, bodies, and URLs.

Phishing emails were grouped into the following thematic categories:

- **FINANCE**
- **ACCOUNT**
- **SHOPPING**
- **SERVICE**
- **ORGANIZATION**
- **PRIZE**

Legitimate emails were labeled under a unified **SAFE_CONTENT** class.

---

### Final Dataset Characteristics

The final dataset:

- Supports both binary and multi-class classification tasks  
- Preserves class distribution using stratified data splitting  
- Is optimized for Transformer-based language models  
- Reflects realistic and modern phishing attack strategies  

---

## Data Preprocessing

- Email subject and body fields are merged into a single textual input
- Noisy characters, malformed tokens, and numerical artifacts are removed
- Tokenization is performed using the **XLM-RoBERTa tokenizer**
- Fixed maximum sequence length is applied with truncation and padding
- Class labels are converted into numerical format for model training

---

## Model Architecture

- **Text Encoder:** XLM-RoBERTa (Multilingual Transformer)
- **Classifier:** Fine-tuned Transformer-based sequence classifier
- **Explainability Module:** Mistral-based Large Language Model
- **Auxiliary Technical Signals (Explainability Only):**
  - IP-based URLs
  - Suspicious keywords (e.g., login, verify, secure)
  - URL length and structural complexity
  - Unusual top-level domains (TLDs)
  - Redirection and special character patterns

> ⚠️ Technical signals are not used during model training and are included only to enhance explanation quality.

---

## Experimental Results

- **Binary classification accuracy:** **99.21%**
- XLM-RoBERTa outperformed BERT, RoBERTa, ELECTRA, DistilBERT, and mDeBERTa
- Best explainable multi-class configuration: **XLM-RoBERTa + Mistral-7B**
- High recall minimizes false negatives, which is critical in cybersecurity applications

---

## Explainability

The LLM-powered explanation module generates **natural language reports** describing:

- Why an email is classified as phishing or legitimate
- Which linguistic and technical patterns influenced the decision
- How URL characteristics support the prediction

This approach reduces the black-box nature of deep learning models and improves interpretability for security analysts and end users.

---

## Technologies Used

- Python  
- PyTorch  
- Hugging Face Transformers  
- XLM-RoBERTa  
- Mistral LLM  
- Google Colab  
- Flask  

---

## Future Work

- Multi-language phishing detection  
- Integration of network-level security indicators  
- Quantitative evaluation of explanation quality  
- Lightweight models for resource-constrained environments  

---

kalmayıp, phishing içeriklerini kategorize edebilmekte ve kararlarını doğal dilde açıklayabilmektedir. Çalışma, yüksek doğruluk, güçlü bağlamsal analiz ve kullanıcıya yönelik açıklanabilirlik sunan bütüncül bir siber güvenlik çözümü önermektedir.
