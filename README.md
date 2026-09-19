<p align="center">
  <img src="https://huggingface.co/3amthoughts/zenfinance-3b/resolve/main/post-136-hd.png" width="800">
</p>



# 🧘‍♂️ ZenFinance-3B-Agent (GGUF)

ZenFinance-3B is a highly specialized, agentic large language model designed for personal finance applications. Fine-tuned from Llama-3.2-3B-Instruct, this model acts as both a **financial advisor** and a **UI agent**. 

It is trained to "think" before it speaks using `<thought>` tags, and can execute frontend actions (like adding expenses or setting savings goals) by outputting strict JSON inside `<tool_call>` tags.

## ⚡ Model Highlights
* **Architecture:** 3B Parameters (Llama-3.2 base)
* **Format:** GGUF (`q4_k_m` - highly compressed, runs on <3GB RAM)
* **Capabilities:** Financial reasoning, budgeting advice, and structured JSON tool calling.
* **Training:** Fine-tuned using QLoRA via [Unsloth](https://github.com/unslothai/unsloth) on a mixed dataset of 4,000 financial and agentic interactions.

---

## 🛠️ How it Works (Prompting & Output)

To get the model to trigger actions, you must use the standard Llama-3 chat template and include the system prompt defining its tools.

**System Prompt:**
> "You are ZenFinance AI, a minimalist personal finance assistant. You provide calm, objective financial advice and can execute actions using tools."

### Example Interaction

**User:**
> "I just spent $12 on lunch."

**ZenFinance-3B Output:**
```text
<thought>
User spent $12 on lunch. Category: Food. This is an expense.
I will trigger the add_transaction tool to update their dashboard.
</thought>
<tool_call>
{"action": "add_transaction", "amount": 12, "category": "Food", "type": "expense"}
</tool_call>
I've added that $12 food expense to your dashboard.
