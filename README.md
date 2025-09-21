# AI-doctor-Consultant-Deepseek-R1-
This project demonstrates how to take a powerful LLM (DeepSeek-R1), make it domain-specific with LoRA (PEFT), optimize training with Unsloth, and track improvements with WandB, resulting in an efficient AI-powered medical assistant.


📌 Project Overview

I developed an AI Doctor Suggestion System using the DeepSeek-R1 8B parameter model, fine-tuned on a medical reasoning dataset. The system is capable of analyzing clinical queries, applying step-by-step reasoning, and suggesting diagnostic or treatment directions like a medical expert.
link:-https://huggingface.co/deepseek-ai/DeepSeek-R1
🔑 Key Highlights

Base Model: DeepSeek-R1 (Distilled 8B version) → strong reasoning ability for medical Q&A.
link:-https://huggingface.co/deepseek-ai/DeepSeek-R1

Fine-Tuning: Used PEFT (LoRA) to efficiently adapt the model to medical reasoning tasks.
link:-https://huggingface.co/docs/peft/en/index

Libraries Used:

Torch → model training and GPU acceleration.

Hugging Face Transformers → model and tokenizer management.

Unsloth → optimized LLM fine-tuning (memory + speed efficient).

W&B (Weights & Biases) → experiment tracking and visualization.

⚙️ How It Works
1. DeepSeek-R1 Model

A large language model optimized for step-by-step reasoning.

Provides the backbone for medical diagnostics, reasoning, and treatment planning.

2. PEFT with LoRA

Instead of retraining all 8B parameters, I fine-tuned only low-rank adaptation layers inside the transformer (attention + MLP).

LoRA hyperparameters I used:

r = 16, lora_alpha = 16

target_modules = ["q_proj", "k_proj", "v_proj", "o_proj", "gate_proj", "up_proj", "down_proj"]

This made the model faster, cheaper, and domain-specific without losing its reasoning ability.

3. Unsloth Optimization

Allowed me to:

Load the 8B model in 4-bit quantization → fits on smaller GPUs (like Colab T4/A100).

Skip manual tokenization pipelines (Unsloth handles text → tokens internally).

Use gradient checkpointing & memory optimizations to train with limited GPU memory.

4. Weights & Biases (W&B Dashboard)

I connected training to the W&B website, which automatically generated a dashboard.

This dashboard displayed:

Training loss curves, learning rate schedules, and accuracy metrics in real time.

Comparison of multiple runs with different hyperparameters.

A centralized project log for reproducibility and sharing.

The dashboard made it easy to monitor performance and spot issues early during training.

📊 Results

The fine-tuned model successfully answers complex medical reasoning questions with a clear diagnostic thought process.

Example:

Input:
A 61-year-old woman has involuntary urine loss during coughing/sneezing but no leakage at night. What would cystometry most likely reveal?

Output:
Normal detrusor contractions, low residual volume → consistent with stress incontinence.

🚀 Future Improvements

Deploy as a Streamlit web app for interactive medical Q&A.

Extend dataset with multi-lingual medical reasoning.

Integrate retrieval-augmented generation (RAG) for up-to-date medical guidelines.
