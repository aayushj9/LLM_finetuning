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
  
- The expected response is kept as the target label.

- This structure is converted into a format compatible with Hugging Face datasets for efficient processing.

---

### 2. Model and Tokenizer Loading

- The pretrained `google/flan-t5-small` model and its tokenizer are loaded. This model is a sequence-to-sequence transformer designed to generate text based on given instructions and inputs.

---

### 3. Tokenization

- Both the input text and the output labels are tokenized using the tokenizer.
- Tokenization includes padding and truncation to a fixed maximum sequence length to ensure consistent input sizes.
- The tokenized inputs and labels are aligned for supervised training.

---

### 4. Defining Training Configuration

- Training arguments are set, including batch size, number of epochs, logging frequency, and output directories.
- These configurations control how the model will be fine-tuned, including how often the model saves progress and reports status.

---

### 5. Model Fine-Tuning

- The `Trainer` class from Hugging Face is used to manage the training loop.
- The model is trained on the tokenized dataset, adjusting its parameters to better map airline-related inputs to correct responses.

---

### 6. Model Evaluation

- After training, the fine-tuned model is evaluated by generating answers to the same set of instructions and inputs.
- The generated responses are compared against the expected outputs using a simple keyword matching technique.
- Overall accuracy is calculated as the proportion of examples where the model’s response contains the expected key terms.

---


## Challenges & Reasons for Low Accuracy (~10%)

1. **Small Dataset Size**  
 The dataset contains only about 30 examples, which is insufficient for effective fine-tuning of even a small transformer model.

2. **Limited Training Epochs and Batch Size**  
 Only 5 epochs with a batch size of 2 might not allow the model to converge well or generalize.

3. **Simple Keyword Matching for Evaluation**  
 The accuracy calculation relies on a simple keyword match, which can underestimate the quality if the model produces correct but paraphrased or semantically similar responses.

4. **Model Size Constraints**  
 `google/flan-t5-small` is a relatively small model with limited capacity, restricting its ability to learn complex language patterns and domain knowledge from limited data.

5. **No Data Augmentation or Diversity**  
 The training examples, while varied, are limited in number and might not cover enough variations of queries, leading to poor generalization.

6. **Overfitting Risk**  
 With such a small dataset, the model can easily overfit on training data without truly learning to generalize responses.

7. **Lack of Validation Set**  
 There’s no separate validation or test set to tune hyperparameters or prevent overfitting, reducing training effectiveness.

8. **Truncation and Padding Effects**  
 Fixed max length tokenization can truncate important information or add unnecessary padding, affecting learning quality.

9. **Absence of Advanced Fine-Tuning Techniques**  
 Techniques like learning rate schedulers, early stopping, or data mixing were not applied, which can improve performance.

10. **Simplistic Input Formatting**  
  Although instructions and inputs are combined, the model might benefit from more contextual prompts or better formatting for clarity.

11. **No Use of Preprocessing or Cleaning of Input Text**  
  Variations in user input (spelling, grammar, phrasing) are not addressed, potentially confusing the model.

12. **Limited Hyperparameter Tuning**  
  No experimentation with learning rate, optimizer choice, or other parameters to optimize fine-tuning.

13. **Evaluation on Training Data Only**  
  Evaluating on the same data used for training does not provide a robust measure of generalization.

14. **Inherent Model Biases and Pretraining Domain**  
  The base Flan-T5 model is trained on general language tasks and might not have sufficient prior knowledge of airline-specific jargon.

15. **Simple Labeling Strategy**  
  Using direct output text as labels without additional conditioning or token alignment might limit model’s understanding of the task.

---

## Summary

Fine-tuning a small model like `google/flan-t5-small` on a limited dataset with minimal hyperparameter tuning and evaluation can result in low accuracy. To improve, one should consider:

- Increasing dataset size and diversity.
- Using more advanced fine-tuning strategies.
- Employing better evaluation metrics.
- Experimenting with larger or domain-adapted models.

---

## Next Steps

- Expand dataset with more examples and variations.
- Implement validation and test splits.
- Explore larger or more domain-specific pretrained models.
- Apply data augmentation and more sophisticated training schedules.
- Use semantic similarity metrics or human evaluation for better accuracy assessment.

---
