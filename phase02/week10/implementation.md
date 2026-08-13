## Tech Stack and Key Components

1. LangChain for orchestration
2. Mistral Embeddings for vector representation
3. MongoDB Atlas Vector Search as the vector database
4. GPT-4o-mini for test case generation
5. Rule-based moderation for sensitive-data detection, masking, and blocking
6. Sarvam speech-to-text API for voice input
7. Multimodal input support for text, voice, and uploaded requirements
8. Session isolation to keep each conversation and generated test cases independent

## Moderation and Context Flow

One of the interesting parts of this project was designing the flow around moderation and context:

```text
Input ➔ Moderation ➔ Query Processing ➔ Embedding ➔ Vector Search ➔ Relevant Context ➔ LLM ➔ Test Cases
```

## Voice Input Architecture

For voice input, the architecture stays simple:

```text
Voice ➔ Sarvam STT ➔ Text ➔ Existing RAG Pipeline
```
