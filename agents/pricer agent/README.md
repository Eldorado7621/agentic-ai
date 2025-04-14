# 💰 Pricer Service (LLM-based Price Estimator)

A Python service that uses a fine-tuned LLaMA 3.1 model to estimate prices from natural language descriptions. Built for fast, GPU-powered, containerized inference using HuggingFace Transformers and PEFT. It is deployed on using serverless Infrastructure as a Code technology on Modal cloud.

---

## 🚀 Features

- Uses **Meta-Llama 3.1-8B** as the base model.
- Fine-tuned on domain-specific pricing data.
- Runs on **Modal.com** with GPU acceleration (T4).
- 4-bit quantized for memory efficiency via **BitsAndBytes**.
- Easy to deploy, scalable, and ready for production.

---

## 🛠️ Tech Stack

- 🧠 [HuggingFace Transformers](https://huggingface.co/transformers/)
- ⚡ [Modal](https://modal.com/) for deployment
- 🔢 [PEFT](https://huggingface.co/docs/peft/) for efficient fine-tuning
- 🧮 BitsAndBytes for quantized inference

---

## 📦 Installation

> Make sure you have a [Modal account](https://modal.com) and the CLI installed.

```bash
pip install modal
```

---

## 🧪 Usage

### 1. **Deploy the Service**

```bash
Can be deployed by using the specialist agent class defined in the specialist_agent.py file
```

### 2. **Run a Pricing Query**

You can call the `price()` method with any product or service description:

```python
from agents.specialist_agent import SpecialistAgent

agent = SpecialistAgent()
agent.price("A high-end gaming laptop with RTX 4090 and 32GB RAM")

```

Output might look like:

```
Price is $2499
```

---

## 🧰 Configuration

Environment variables / secrets:
- `hf-secret`: your HuggingFace token (created in Modal under Secrets)

Constants defined:
- `BASE_MODEL`: `"meta-llama/Meta-Llama-3.1-8B"`
- `FINETUNED_MODEL`: `"eldorado762/pricer-2025-03-13_13.04.39"`
- `GPU`: `"T4"`

---

## 🔐 Secrets

Make sure to set up your HuggingFace secret in Modal:

```bash
modal secret create hf-secret
```

---

## 📁 Directory Structure

The model is cached to the following locations:

- `hf-cache/meta-llama/Meta-Llama-3.1-8B`
- `hf-cache/eldorado762/pricer-2025-03-13_13.04.39`

---

## 🧼 Example Prompt

The model receives prompts like this:

```
How much does this cost to the nearest dollar?

A high-end espresso machine with dual boiler and PID temperature control.

Price is $
```

The model then generates the estimated price.

---

## 🧠 Developer Notes

- All logic is encapsulated in the `Pricer` class.
- Download + load model logic is separated for speed and caching.
- Model inference is handled via `generate()` with a short token window.

---

## 📜 License

MIT © 2025

---

## 🙌 Credits

Based on the instructions the LLM course by Ed-doner [@ed-donner](https://huggingface.co/ed-donner) 💡
