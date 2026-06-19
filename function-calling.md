# 07 — Function Calling (Tool Use)

## 📖 Concept

LLMs are trained on static data — they don't know what's happening *right now*. **Function Calling** lets an AI "reach out" to external systems to get real-world data instead of guessing.

### How it works:

```
User: "What's the stock price of Apple?"
    ↓
LLM recognizes it needs live data
    ↓
Calls: get_stock_price(ticker="AAPL")
    ↓
API returns: $213.45
    ↓
LLM responds: "Apple is currently trading at $213.45."
```

Without tool calling → AI would guess or hallucinate a price.
With tool calling → AI becomes a reliable **Data Agent**.

### What can AI call?
- Live APIs (weather, stock prices, flight status)
- Your SQL database
- Internal business systems (ERP, CRM, inventory)
- PySpark / data pipelines

---

## 🛒 Domain Example — Live Inventory Checker

**Scenario:** A retail chatbot on your e-commerce site needs to answer: *"Is the blue Nike Air Max size 10 in stock?"*

**Without function calling:**
```
AI: "Nike Air Max is a popular shoe. It is usually available in most sizes." ← Hallucinated
```

**With function calling:**
```python
# Tool defined in system
def check_inventory(product_id: str, size: str, color: str) -> dict:
    return db.query(f"SELECT stock FROM inventory WHERE sku='{product_id}' ...")

# Conversation
User: "Is the blue Nike Air Max size 10 available?"
AI calls: check_inventory(product_id="NIKE-AM-BLU", size="10", color="blue")
Returns: {"stock": 3, "warehouse": "Chicago"}
AI responds: "Yes! We have 3 pairs of blue Nike Air Max in size 10, shipping from Chicago."
```

**Extended scenario — "October weather" problem:**
User: *"What will the weather be like on October 15, 2027?"*
- Too far → no forecast API can answer
- AI pivots: calls `get_climate_averages(location, month="October")` instead
- Responds honestly: *"I can't predict that specific day, but October in your city averages 58°F with occasional rain."*

This is **honesty + utility** — the AI doesn't hallucinate, it uses the best tool available.

---

## ✅ TIL

> Function calling is what separates a chatbot from an agent. A chatbot talks. An agent *acts* — by reaching into real systems to get real answers.
