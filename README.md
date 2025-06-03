# LLM finetuning

# Airline_Chatbot_FineTuning

A Python-based fine-tuning project for an airline customer support chatbot using open-source Large Language Models (LLMs) with Hugging Face PEFT and LoRA techniques.

---

# 🛫 AI-Powered Airline Chatbot with Fine-Tuned LLM

This project fine-tunes a powerful open-source LLM on airline-specific customer queries to build a chatbot capable of handling tasks like booking flights, checking flight status, baggage policies, refunds, and more.

---

## 📌 Features

- Fine-tune an open-source LLM model (`mistralai/Mistral-7B-Instruct-v0.1` or similar)
- Use PEFT (LoRA) for parameter-efficient, low-resource fine-tuning
- Custom dataset with 30+ real-world airline customer queries
- Evaluate fine-tuned model accuracy on test queries
- Easy-to-understand example notebook for training and inference
- Ready for deployment as a chatbot backend

---

### ✅ Prerequisites

- Python 3.8+
- GPU with CUDA support (for faster fine-tuning; CPU also works but slower)
- Hugging Face `transformers`, `datasets`, `peft`, `accelerate`, `trl` libraries
- Internet connection for downloading pre-trained models

---

## 🚀 Getting Started

Follow these steps to run fine-tuning locally or on Google Colab.

---

### 📥 1. Clone the Repository

```bash
git clone https://github.com/yourusername/Airline_Chatbot_FineTuning.git
cd Airline_Chatbot_FineTuning
