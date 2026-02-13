
# 🦙 Fine-Tuning Llama-3: Semantic Customer Service Helper


## 💼 Business Case

In high-volume customer service environments, up to 70% of incoming inquiries are repetitive variations of existing FAQs. Manually identifying these duplicates is labor-intensive and leads to delayed response times.

This project solves this by fine-tuning Llama-3 to perform Semantic Similarity Classification. 

 `The Solution`: **An automated "Agent Helper" that instantly matches new customer tickets to the correct historical resolution.**

Impact: 
- Reduces Time-to-First-Response (TTFR).
- Ensures Brand Consistency across multiple agents.
-  Allows human specialists to focus on complex, non-standard cases where they provide the most value.


## Technical Overview

This project fine-tunes the Llama-3 8B model using Instruction-based Supervised Fine-Tuning (SFT).

Base model used: `base_model: unsloth/llama-3-8b-bnb-4bit`

**Key Technologies:**

- Unsloth: Used for 2x faster training and 70% less VRAM usage.

- QLoRA (4-bit Quantization): Enabled training a high-performance 8B model on a single free-tier Nvidia T4 GPU (16GB).


- Synthetic Reasoning: Used a dataset enriched with GPT-4 generated explanations to implement Chain-of-Thought (CoT), forcing the model to explain its logic before providing a label.

- Neptune.ai: Integrated for real-time experiment tracking and hardware monitoring.
Hardware & Optimization Architecture

>[!NOTE]
>  This model is designed to serve as the "Reasoning Engine" for a larger RAG (Retrieval-Augmented Generation) chatbot system, which can be queried to provide automated answers directly from company documentation

## Roadmap
- [x] Instruction-based Fine-tuning on Llama-3 8B.

- [x] Experiment tracking via Neptune.ai.

- [ ] Next Step: Integrate into a Retrieval-Augmented Generation (RAG) pipeline using a Vector Database (Pinecone/Chroma) to query live company PDFs.

- [ ] Deploy via FastAPI as a microservice for existing CRM systems.
