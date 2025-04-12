# 🤖 Frontier Agent – Price Estimator with RAG + OpenAI

The **Frontier Agent** is an AI-powered tool designed to estimate the price of a described item using a **Retrieval-Augmented Generation (RAG)** approach. It finds similar products from a vector database (ChromaDB), builds a custom prompt, and queries **OpenAI’s GPT model** for a contextualized price estimate.

---

## 🚀 Features

- Retrieves top-5 semantically similar products using **SentenceTransformers** and **ChromaDB**
- Builds context-aware prompts for accurate price estimation
- Uses **OpenAI GPT-4o-mini** for inference
- Clean object-oriented design via a custom `Agent` class
- Includes utility functions for parsing and formatting price predictions

---

## 📁 File Structure

```bash
frontier_agent.py        # Main agent logic
items.py                 # Custom item object definitions
testing.py               # Testing framework (assumed)
agents/agent.py          # Base Agent class
```

---

## 🧰 Dependencies

Make sure to install these Python packages before running:

```bash
pip install openai sentence-transformers chromadb datasets
```

You may also need local modules:
- `items.py`
- `testing.py`
- `agents/agent.py`

---

## 🧠 How It Works

1. **Input**: A product description (`str`)
2. **RAG Retrieval**: The agent searches for similar items in ChromaDB using vector embeddings.
3. **Prompt Construction**: Embeds relevant context into a structured prompt.
4. **LLM Inference**: Sends a system + user message to OpenAI with context and returns a price estimate.
5. **Output**: Returns a floating-point estimate.

---

## 🧪 Example Usage

```python
from frontier_agent import FrontierAgent

# Assume you have a ChromaDB collection ready
agent = FrontierAgent(collection)

description = "A lightweight electric scooter with 25-mile range and top speed of 20mph"
estimated_price = agent.price(description)

print(f"Estimated price: ${estimated_price:.2f}")
```

---

## 🧬 Key Components

### `make_context(similars, prices)`
Creates a formatted prompt including similar items and their prices.

### `messages_for(description, similars, prices)`
Constructs the full OpenAI-compatible message list for the API call.

### `find_similars(description)`
Queries the ChromaDB vector store for the most similar items.

### `get_price(string)`
Parses the model output to extract the price value.

---

## 🔐 OpenAI API Key

Ensure your OpenAI key is configured via environment variables or the OpenAI SDK.

```bash
export OPENAI_API_KEY="your-key-here"
```

---

## 🧩 To Do / Improvements

- Add support for batch processing
- Include uncertainty/confidence scores
- Connect to real-time product catalogs or APIs

---

## 📜 License

MIT © 2025

---

## 🙌 Acknowledgments

Powered by:
- [OpenAI](https://openai.com/)
- [ChromaDB](https://www.trychroma.com/)
- [Sentence Transformers](https://www.sbert.net/)
