# Fine-Tuning and Reinforcement Learning with Unsloth AI
### A Hands-on Series of Colab Notebooks (Colab 1–5)

This repository demonstrates **modern LLM training workflows** using [Unsloth AI](https://unsloth.ai) — a lightweight, memory-efficient framework for fine-tuning and reinforcement learning on open-weight language models.

---

## Overview

| Colab | Title | Core Concept | Model | Key Technique |
|:------|:-------|:--------------|:--------|:---------------|
| [Colab 1](#colab-1-full-finetuning) | Full Finetuning | Train **all** model parameters on a custom dataset | `SmolLM2-135M` | Full Finetuning |
| [Colab 2](#colab-2-lora-finetuning) | LoRA Finetuning | Parameter-efficient finetuning with **Low-Rank Adapters** | `SmolLM2-135M` | LoRA / PEFT |
| [Colab 3](#colab-3-reinforcement-learning-dpo) | Reinforcement Learning (DPO) | Learn from **preferred vs rejected** responses | `SmolLM2-135M` | DPO (Direct Preference Optimization) |
| [Colab 4](#colab-4-reinforcement-learning-grpo) | Reinforcement Learning (GRPO) | Train reasoning ability via **chain-of-thought rewards** | `SmolLM2-135M` | GRPO (Reasoning RL) |
| [Colab 5](#colab-5-continued-pretraining) | Continued Pretraining | Teach model a **new language or domain** | `SmolLM2-135M` | Domain Adaptation / Language Modeling |

---

## Colab 1 — Full Finetuning
**Goal:** Fine-tune all model weights on a small instruction-following dataset.

- Uses: `SmolLM2-135M`  
- Dataset: Alpaca (instruction–response pairs)  
- Method: `full_finetuning=True` with Unsloth  
- Task examples: basic chat or code completion  
- Output: fully fine-tuned checkpoint saved and ready for Hugging Face upload.

**Key takeaway:** Full finetuning is accurate but VRAM-heavy — use only for small models.

---

## Colab 2 — LoRA Finetuning
**Goal:** Achieve similar performance using **LoRA (Low-Rank Adapters)**.

- Keeps base model frozen; trains tiny adapter matrices.  
- Memory usage drops by ~90%.  
- Ideal for quick prototyping and multi-domain fine-tunes.  
- Can export to **Ollama** or **Hugging Face** easily.  
- Same dataset and task setup as Colab 1.

**Key takeaway:** LoRA = same quality, fraction of cost.

---

## Colab 3 — Reinforcement Learning (DPO)
**Goal:** Improve model preference alignment using **Direct Preference Optimization (DPO)**.

- Dataset: prompt + chosen (preferred) + rejected (non-preferred)  
- Reference model: frozen copy of base  
- Policy model: LoRA-tuned version updated via preference loss  
- Loss: `−log σ(β * [(Δpolicy) − (Δreference)])`  
- Result: model learns to prefer better answers (e.g., safer, more helpful).

 **Key takeaway:** DPO teaches *preferences* directly from comparisons — no reward model required.

---

## Colab 4 — Reinforcement Learning (GRPO)
**Goal:** Train **reasoning models** that generate intermediate “thought” steps before answers.

- Approach: GRPO (Generalized Reinforcement Policy Optimization)  
- Dataset: reasoning problems (math, logic, QA)  
- Reward: correctness of “Final Answer:” + optional chain-of-thought scoring  
- Outputs: improved reasoning and structured responses

**Key takeaway:** GRPO = reinforcement learning for **chain-of-thought reasoning**.

---

## Colab 5 — Continued Pretraining
**Goal:** Teach the model a **new language** or adapt to a specific **domain corpus**.

- Uses unlabeled text (monolingual, domain, or uploaded corpus)  
- Objective: next-token prediction (causal LM)  
- Example: adapt SmolLM2 to Swahili, Tamil, or any custom dataset  
- Optional: run with LoRA for low VRAM, or full finetune for large-scale training

**Key takeaway:** Continued pretraining builds a stronger linguistic foundation before instruction tuning.

---

## Deployment & Export

All notebooks demonstrate how to:
- Save **LoRA adapters** (`adapter_config.json`, `adapter_model.safetensors`)
- Merge adapters into base weights for **standalone inference**
- Push to [ Hugging Face Hub](https://huggingface.co)
- Export to [Ollama](https://ollama.com) for local use

---


