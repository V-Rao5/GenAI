# 08 — AI Cost Optimization

## 📖 Concept

> "What feels cheap in development becomes a major liability when repeated thousands of times per minute."

### The Cost Explosion Pattern

Token prices dropped ~90% over 2023–2024. Yet enterprise AI bills are exploding. Why?

**Agentic AI changed the consumption model:**

```
Old: User asks 1 question → AI answers → done (~500 tokens)

New (Agentic): 
Agent receives task
  → reads entire codebase context     (~20,000 tokens)
  → plans steps                        (~2,000 tokens)
  → executes step 1, re-reads context (~20,000 tokens)
  → executes step 2, re-reads context (~20,000 tokens)
  → ...
Total for ONE task: 100,000+ tokens
```

**The result:** Teams are burning through annual LLM budgets before Q2 ends.

### Cost Discipline Strategies

| Strategy | How |
|----------|-----|
| **Prompt optimization** | ROCCO framework — ask for short answers when that's all you need |
| **Model right-sizing** | Don't use GPT-4 when GPT-3.5 or a local model will do |
| **Limit output length** | `max_tokens=100` when you only need a sentence |
| **Cache responses** | Identical queries → return cached answer, don't re-call the API |
| **Local inference** | Run smaller models locally for repetitive internal tasks |
| **Token tracking** | Monitor per-feature token usage, not just total bill |

---

## 💼 Domain Example — SaaS Startup AI Budget

**Scenario:** A startup builds an AI feature that summarizes support tickets. It works great in testing. Then they launch.

**Day 1 in production:**
- 500 tickets/day
- Each summary prompt: ~800 tokens in, ~300 tokens out = 1,100 tokens
- Daily cost: 500 × 1,100 = 550,000 tokens → ~$1.65/day with GPT-4 ✅

**Month 3 — agentic upgrade added:**
- Agent now reads full ticket history (10 prior tickets) before summarizing
- Each call: ~8,000 tokens in, ~300 out = 8,300 tokens
- Daily cost: 500 × 8,300 = 4,150,000 tokens → ~$12.45/day
- Monthly: ~$375 → budgeted $200 ❌

**Fix applied:**
1. Summarize history once → cache it → don't re-read raw tickets every call
2. Switch from GPT-4 to GPT-4o-mini for routine summaries (90% cheaper)
3. Add `max_tokens=150` since summaries don't need to be long
4. Result: back to ~$60/month ✅

---

## ✅ TIL

> AI innovation is not only about capability — it's about discipline. Track token usage per feature, not just as a total bill. The feature you're proudest of might be your most expensive mistake.
