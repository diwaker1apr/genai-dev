## Generative AI Fundamentals  
### Lesson 1: What is Generative AI?

Traditional AI is designed to **analyze, classify, or predict**.

Examples:

* Spam detection
* Image classification
* Fraud detection

Generative AI, on the other hand, **creates new content** based on patterns it learned from data.

It can generate:

* Text
* Images
* Code
* Audio
* Video

Examples:

* ChatGPT
* Claude
* Gemini
* GitHub Copilot  

# How Does a Large Language Model (LLM) Work?

A **Large Language Model (LLM)** is an artificial intelligence model trained on massive amounts of text data to understand and generate human-like language.

At its core, an LLM works by **predicting the next most likely token** (a word or part of a word) based on the sequence of tokens it has already seen.

For example, given the prompt:

```text
The capital of France is
```

the model predicts the next token:

```text
Paris
```

It then continues predicting one token at a time until it generates a complete response.

## How an LLM Learns

LLMs are trained on billions or even trillions of tokens collected from books, articles, websites, documentation, and publicly available code. During training, the model learns statistical patterns and relationships between words, phrases, and concepts rather than memorizing facts like a database.

This allows the model to:

* Answer questions
* Generate text
* Write code
* Summarize documents
* Translate languages
* Assist with reasoning tasks

## The LLM Workflow

1. The user enters a prompt.
2. The prompt is converted into tokens.
3. The model processes the tokens using its learned parameters.
4. It predicts the most probable next token.
5. The process repeats until the response is complete.

```text
User Prompt
      │
      ▼
Tokenization
      │
      ▼
LLM Processing
      │
      ▼
Next Token Prediction
      │
      ▼
Generated Response
```

## Key Takeaway

An LLM does not think or understand information like a human. Instead, it generates responses by predicting the most likely sequence of tokens based on patterns learned during training. Despite this simple underlying mechanism, the scale of the training data and model parameters enables LLMs to produce remarkably useful and coherent outputs.
