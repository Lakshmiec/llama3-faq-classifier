
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

## 📊 Training Results & Model Performance

**Model Configuration**

Base Model: `unsloth/llama-3-8b-bnb-4bit`

Total Parameters: `8,072,204,288`

Trainable Parameters: `41,943,040 (0.52%)`

Quantization: `4-bit QLoRA`

Dataset Size: `1,000 samples`

Epochs: `2`

Batch Size: `2`

Gradient Accumulation: `1`

Hardware: `Single NVIDIA T4 (16GB)`


**Analysis**:

Validation loss reached its minimum (~0.385) at approximately Step 480–500 (≈1 epoch). Beyond Step 510, validation loss began a gradual increase, ultimately reaching 0.4016 by the end of training, while training loss continued to decline.

This divergence indicates the onset of overfitting. Therefore, early stopping at approximately 1 epoch would likely maximize generalization performance on unseen data.

## Roadmap
- [x] Instruction-based Fine-tuning on Llama-3 8B.

- [x] Experiment tracking via Neptune.ai.

- [ ] Next Step: Integrate into a Retrieval-Augmented Generation (RAG) pipeline using a Vector Database (Pinecone/Chroma) to query live company PDFs.

- [ ] Deploy via FastAPI as a microservice for existing CRM systems.
