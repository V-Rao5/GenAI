# 01 — Tokens

## 📖 Concept

ChatGPT (and all LLMs) don't read text like humans. They first break your input into **tokens** using a tokenizer.

A token can be:
- a full word → `hello`
- part of a word → `token` + `izer`
- punctuation → `.`, `,`
- a space or newline

**Why it matters:**
Every prompt + response costs tokens. More tokens = faster rate limit usage + higher API costs.

**The trick:** Write clear, concise prompts instead of long explanations.

---

## 🏪 Domain Example — E-commerce Product Descriptions

**Scenario:** You run an online store and want AI to write product descriptions.

**Wasteful prompt (high tokens):**
```
I would like you to please write me a really nice, detailed, and engaging product description for a red cotton t-shirt that is size medium, made in India, and costs $19.99. Make sure it sounds good and covers everything a buyer might want to know.
```
→ ~60 tokens used just for the instruction.

**Optimized prompt (low tokens):**
```
Write a 2-sentence product description.
Product: Red cotton t-shirt | Size: M | Origin: India | Price: $19.99
```
→ ~30 tokens. Same quality output, half the cost.

**Lesson:** In e-commerce, you might generate 10,000 descriptions/day. Cutting token waste in half = cutting your AI bill in half.

---

## ✅ TIL (Today I Learned)

> Tokens are not words. A 10-word prompt can be 15+ tokens. Always check with [OpenAI Tokenizer](https://platform.openai.com/tokenizer).
