# 05 — RAG (Retrieval-Augmented Generation)

## 📖 Concept

RAG transforms a static LLM into a **dynamic, factual researcher** by grounding it in your specific data.

### How it works in 3 steps:

```
User Query
    ↓
[1] RETRIEVAL — Search vector DB for relevant chunks
    ↓
[2] AUGMENTATION — Inject those chunks into the prompt
    ↓
[3] GENERATION — LLM answers based on retrieved facts
```

### Why not just fine-tune?
| | RAG | Fine-tuning |
|--|-----|-------------|
| Update knowledge | Swap documents ✅ | Retrain model ❌ (expensive) |
| Hallucination risk | Low (grounded in facts) | Higher |
| Citations | Yes ✅ | No |
| Cost | Low | Very high |

---

## 🏢 Domain Example — Company Policy Q&A Bot

**Scenario:** A 500-person company wants employees to get instant answers about HR policies, IT procedures, and benefits — without emailing HR.

**Without RAG:**
```
Employee: "How many sick days do I get?"
AI: "Typically employees get 5-10 sick days..." ← Generic, possibly wrong
```

**With RAG (documents loaded: Employee Handbook 2024.pdf):**
```
[Retrieval] → Finds chunk: "Full-time employees receive 12 sick days per calendar year..."
[Augmentation] → Injects that chunk into the prompt
[Generation] → "According to your 2024 Employee Handbook, you receive 12 sick days per year."
```

**The anchor word problem (real pitfall):**
If an employee asks *"What's the policy?"* — too vague. The vector distance is too high, wrong chunk is retrieved.
If they ask *"What's the sick day policy?"* — the word "sick day" acts as a mathematical anchor, pulling the right chunk.

**Lesson:** Teach employees to ask specific questions. Or use query expansion to add context automatically.

---

## ✅ TIL

> RAG failure is almost always a *retrieval* problem, not a generation problem. If the AI gives a wrong answer, check what chunk was actually retrieved first.
