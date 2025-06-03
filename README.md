# Fine-Tuning with Google Flan-T5

This project fine-tunes the **`google/flan-t5-small`** language model on a custom airline policy and FAQ dataset to build a chatbot capable of answering various airline-related queries such as flight booking, status, baggage policies, cancellations, and more.

---

## Overview

The goal is to teach a pretrained sequence-to-sequence model to understand instructions and user inputs related to airline services and generate relevant, accurate responses.

---

## Dataset

The dataset consists of multiple examples, where each example contains:

- **Instruction**: A description of the user’s intent (e.g., "Book a flight").
- **Input**: The actual user query (e.g., "I want to book a flight from Delhi to Dubai on 15 July").
- **Output**: The expected chatbot response (e.g., "Sure! Booking a flight from Delhi to Dubai on 15 July. Please confirm your time preference.").

This dataset is formatted to cover a wide range of airline-related scenarios, including flight status, baggage rules, cancellations, seat preferences, refunds, and more.

---

## Step-by-Step Process

### 1. Data Preparation and Preprocessing

- The instruction and user input are combined into a single input text prompt in the format:
  
