
# Multi-Source Customer Support Agent

An AI-powered customer support agent built with Python. It answers queries by retrieving data from:
- a SQLite database (structured data)
- a Markdown knowledge base (unstructured data)

The agent routes queries to appropriate tools without generating raw SQL.

## Features

| Query Type | Tool | Data Source |
|-----------|------|------------|
| Order status | `search_orders` | SQLite |
| Product search | `search_products` | SQLite |
| Policies / FAQs | `search_knowledge_base` | Markdown |
| Warranty check | `check_warranty` | SQLite |

## Project Structure

Multi-Source-Customer-Agent/
│
├── Multi Source Customer Agent.ipynb
│
├── resources/
│   ├── data/
│   │   ├── customer_support_sample.json
│   │   └── knowledge_base/
│   │       ├── return_policy.md
│   │       ├── shipping_info.md
│   │       ├── faq.md
│   │       └── pricing.md
│   │
│   └── prompts/
│       └── customer_support_agent_instructions.txt
│
└── README.md

## Setup

### 1. Upload resources
Place the `resources/` folder in your Google Drive:

```
My Drive/resources/
```

### 2. Open in Colab
- Go to Colab
- Open notebook from GitHub


### 3. Run
```
Runtime → Run All
---

### 4. Test

```python
run_agent("What's the status of order #1001?")
run_agent("Do you have laptops in stock?")
run_agent("What is your return policy?")
run_agent("Is my Ergonomic Chair from 2024-06-20 under warranty?")
```
## Tools

### search_orders
Fetch orders by ID, email, or status

### search_products
Search products by category, keyword, or stock

### search_knowledge_base
Search Markdown documents by keyword relevance

### check_warranty
Returns warranty status based on:
- Electronics → 12 months  
- Furniture → 24 months  
- Accessories → 6 months  

---

## Tech Stack

- Python
- SQLite (in-memory)
- Pydantic
- Transformers (distilgpt2)
- Google Colab

---

## Limitations

- Uses keyword-based routing (no real tool-calling)
- Fallback LLM is weak (distilgpt2)
- Database resets on restart

---

## Author

Akshat Mankar  
NMIMS Shirpur  
GitHub: 17akshatt  

---

## Notes

Use relative paths in code:
```python
RESOURCES = pathlib.Path(".")
```
