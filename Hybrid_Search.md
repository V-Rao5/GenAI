# 10 — Hybrid Search

## 📖 Concept

Modern AI search doesn't choose between keywords or meaning — it uses **both**, orchestrated by an LLM.

### The Hybrid Blueprint

```
User Query
    ↓
┌──────────────────────────────────────┐
│  Sparse (Keyword) Search             │  → Exact matches: names, dates, prices
│  Dense (Semantic) Search             │  → Intent, synonyms, concepts
└──────────────────────────────────────┘
                    ↓
         LLM as Orchestrator
         → Weighs both result streams
         → Filters noise
         → Synthesizes one accurate answer
```

| Search Type | Strengths | Weakness |
|------------|-----------|----------|
| **Sparse (BM25/keyword)** | Exact facts, proper nouns, codes | Misses synonyms, intent |
| **Dense (vector/semantic)** | Understands meaning, context | Can miss specific terms |
| **Hybrid** | Best of both | Slightly more complex to set up |

---

## ⚖️ Domain Example — Legal Document Search

**Scenario:** A law firm's AI assistant searches across 50,000 case files and contracts.

**Keyword-only search fails when:**
```
Attorney searches: "agreement to not compete"
→ Misses documents that say "non-compete clause" or "restrictive covenant"
→ Returns 0 results ❌
```

**Semantic-only search fails when:**
```
Attorney searches: "Case No. 2021-CV-04892"
→ Semantic model sees this as generic text, not a unique identifier
→ Returns loosely related cases ❌
```

**Hybrid search wins:**
```
Attorney searches: "non-compete agreements for software engineers in California 2021"

Sparse layer:  → Finds: "non-compete", "California", "2021"  (exact anchors)
Dense layer:   → Finds: "restrictive covenant", "tech employee", "CA jurisdiction" (synonyms/intent)

LLM orchestrator:
→ Merges both result sets
→ Ranks by relevance to the full query
→ Returns: "Here are 8 relevant contracts. 3 were ruled unenforceable under CA law."
```

**Result:** Associates find precedents in seconds instead of hours of manual searching.

---

## ✅ TIL

> The future of search isn't keywords vs. AI — it's keywords *and* AI working together. Sparse search is your anchor; dense search is your intuition. The LLM is the lawyer that reads both and makes the call.
