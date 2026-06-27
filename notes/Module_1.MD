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

## Key Concepts
1. Tokens

LLMs don't read whole sentences. They process tokens, which are chunks of text.

For example:

My pet is amazing!

might be split into tokens like:

```
My    
pet   
is  
amazing  
!  
 ```

A token can be:

* Part of a word
* A whole word
* Punctuation
* A number

Different models use different tokenizers, so the exact split varies.  
## 2. Context Window

Every Large Language Model (LLM) has a limit on the amount of information it can process in a single interaction. This limit is known as the **context window**.

The context window includes everything the model considers when generating a response, such as:

* Your current prompt
* Previous conversation history
* Documents or files you provide
* The model's own generated responses

The size of the context window is measured in **tokens**, not words. Different LLMs support different context window sizes, ranging from a few thousand tokens to hundreds of thousands or even millions of tokens.

### Why It Matters

The context window determines how much information the model can "remember" during a conversation or while processing a document.

For example:

* A larger context window allows the model to analyze lengthy documents, books, or extended conversations.
* A smaller context window may require splitting large documents into smaller chunks before processing.

If the total number of tokens exceeds the model's context window, older information may be truncated (removed), or the request may fail, depending on the model and API being used.

### Example

Suppose an LLM has a context window of **8,000 tokens**.

* Your prompt: **1,000 tokens**
* Conversation history: **3,500 tokens**
* Attached document: **2,500 tokens**
* Expected response: **1,500 tokens**

Total: **8,500 tokens**

Since this exceeds the context window, the model may discard older conversation history or reject the request.

### Key Takeaway

The context window defines the maximum amount of information an LLM can consider at one time. Understanding this concept is essential when building AI applications that work with long conversations, documents, or Retrieval-Augmented Generation (RAG) systems.  

## 3. Parameters

During training, a Large Language Model (LLM) learns billions—or even trillions—of numerical values called **parameters**. These parameters represent the knowledge the model acquires by identifying patterns and relationships in the training data.

Rather than storing facts like a traditional database, the model encodes statistical relationships within these parameters, enabling it to generate coherent and contextually relevant responses.

### Key Points

* Parameters are the internal values the model adjusts during training.
* They are not manually programmed; they are learned automatically from vast amounts of data.
* A larger number of parameters generally allows the model to capture more complex language patterns.
* However, the number of parameters alone does not determine a model's quality. Factors such as model architecture, training data, optimization techniques, and fine-tuning also have a significant impact on performance.

### Key Takeaway

Parameters form the "knowledge" of an LLM by encoding patterns learned from data. While models with more parameters are often more capable, overall performance depends on multiple factors beyond parameter count.

---

## 4. Temperature

**Temperature** is a model parameter that controls the randomness and creativity of an LLM's responses. It influences how the model selects the next token during text generation.

A lower temperature makes the output more predictable and deterministic, while a higher temperature encourages more diverse and creative responses.

### Common Temperature Values

| Temperature   | Behavior                             | Best For                                      |
| ------------- | ------------------------------------ | --------------------------------------------- |
| **0.0**       | Highly deterministic and consistent  | Code generation, mathematics, factual answers |
| **0.2 – 0.5** | Mostly factual with slight variation | Technical documentation, tutorials, Q&A       |
| **0.7 – 1.0** | Creative and diverse                 | Brainstorming, storytelling, content writing  |

### Examples

**Low Temperature (0.2)**

Prompt:

> Suggest a Python variable name for storing user age.

Possible response:

```python
user_age
```

The response is straightforward and consistent.

**High Temperature (0.9)**

Prompt:

> Suggest a name for an AI startup.

Possible responses:

* NeuralSpark
* PromptForge
* QuantumMind AI
* NovaGen Labs
* IntelliCraft

The responses are more varied and imaginative.

### When to Use Different Temperatures

Use a **low temperature** for:

* Writing code
* Solving mathematical problems
* Technical documentation
* API responses
* Data extraction

Use a **high temperature** for:

* Creative writing
* Brainstorming ideas
* Marketing content
* Storytelling
* Product name generation

### Key Takeaway

Temperature controls the balance between consistency and creativity. Choosing the appropriate temperature depends on the task: use lower values for accuracy and reliability, and higher values when diverse or creative output is desired.


## 5. Hallucinations

A **hallucination** occurs when a Large Language Model (LLM) generates information that appears convincing and plausible but is actually incorrect, fabricated, or unsupported by facts.

Unlike a traditional database, an LLM does not retrieve verified information. Instead, it predicts the next most likely token based on patterns learned during training. As a result, it may occasionally produce responses that sound accurate but are false.

### Example

Suppose an LLM responds:

> "AWS released Service X in 2022."

If no such service exists or it was never released in 2022, this response is considered a hallucination.

### Why Do Hallucinations Occur?

Hallucinations can happen for several reasons:

* The model lacks knowledge about the topic.
* The prompt is ambiguous or lacks sufficient context.
* The requested information is recent and was not included in the model's training data.
* The model prioritizes generating fluent text over verifying factual accuracy.

### How to Reduce Hallucinations

Although hallucinations cannot be completely eliminated, they can be significantly reduced by:

* Writing clear and specific prompts.
* Providing relevant context or reference documents.
* Asking the model to cite sources when appropriate.
* Using **Retrieval-Augmented Generation (RAG)** to supply factual information from external knowledge bases.
* Verifying important responses before relying on them.

### Key Takeaway

LLMs are powerful language generators, but they are not perfect sources of truth. Always validate responses when accuracy is critical, especially in domains such as healthcare, finance, law, and software engineering.

---

# How an AI Application Works

A simple AI application follows this workflow:

```text
User
  │
  ▼
Prompt
  │
  ▼
LLM
  │
  ▼
Generated Response
```

However, production-grade AI applications are usually more sophisticated.

```text
User
  │
  ▼
Application
  │
  ├── Retrieve documents (RAG)
  ├── Call external APIs
  ├── Execute tools or functions
  └── Build the prompt
          │
          ▼
        LLM
          │
          ▼
      Response
```

In this architecture:

* The **application** acts as the orchestrator.
* It retrieves relevant information, calls external services, executes tools, and constructs a well-formatted prompt.
* The LLM generates a response using both the user's request and the additional context provided by the application.

This is the architecture behind many modern AI assistants, chatbots, and enterprise AI applications.

### Key Takeaway

An LLM is only one component of a complete AI system. Real-world applications combine LLMs with external knowledge, APIs, databases, and tools to produce more accurate, reliable, and useful responses.

---

# Prompt Engineering

**Prompt Engineering** is the practice of designing effective prompts that guide an LLM to produce accurate, relevant, and high-quality responses.

A prompt is simply the instruction or input provided to the model. The quality of the prompt has a significant impact on the quality of the output.

### Example

A vague prompt:

> Write Python code.

A better prompt:

> Write a Python function that reads a CSV file, removes duplicate rows, handles missing values gracefully, and includes clear comments.

The second prompt provides:

* A specific task
* Clear requirements
* Context
* Expected behavior

As a result, the model is much more likely to generate useful and accurate code.

### Why Prompt Engineering Matters

Well-crafted prompts help the model:

* Better understand the user's intent.
* Produce more accurate responses.
* Reduce ambiguity.
* Minimize hallucinations.
* Generate outputs in the desired format.

### Key Takeaway

Prompt engineering is one of the most important skills for AI developers. Learning how to communicate effectively with an LLM often has a greater impact on output quality than simply using a more powerful model.

