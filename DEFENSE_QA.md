# Technical Defense & Panel Q&A Guide

**Emganwini Nedbank Hub | Master Project Portfolio**  
*Summative 3 Examination Reference*

---

## 🎯 High-Probability Review Panel Questions & Responses

### Q1: "How do you guarantee your AI system does not provide misleading financial advice or violate the National Credit Act?"
**Answer**:
> *"We implement a defense-in-depth approach. First, our system prompt strictly constrains NedPulse as an educational copilot rather than an automated credit grantor, displaying conspicuous disclaimers on every session. Second, all critical product answers are generated through our RAG pipeline, which forces the model to restrict its responses strictly to retrieved source text from our verified institutional database. If no source chunk scores above our cosine relevance threshold, the model is hardcoded to respond that it does not possess sufficient verified information."*

---

### Q2: "Why choose an in-memory vector index rather than an external managed service like Pinecone or Weaviate?"
**Answer**:
> *"For this capstone deployment, our curated institutional knowledge base contains 2,500+ words partitioned into high-density 500-character chunks with 50-character overlaps. By utilizing an in-memory cosine similarity store, we achieved sub-150ms query latency, zero external API network hop overhead, and zero operational infrastructure cost. For enterprise scaling to millions of documents, the `ragService` is structured so the retrieval engine can be swapped for a pgvector extension in our existing PostgreSQL database or an enterprise Pinecone cluster without altering frontend or controller interfaces."*

---

### Q3: "How does your architecture handle South African POPIA data privacy requirements?"
**Answer**:
> *"Under POPIA, personal information must be collected with consent, protected against compromise, and destroyed upon request. We ensure that passwords are irreversibly salted with bcrypt, sensitive financial attributes (credit scores, monthly income) are accessible only via authenticated JWT tokens, no client transaction data is sent to external LLM training loops, and users maintain the right to delete their conversation histories directly from our database."*

---

### Q4: "How does your system prevent denial-of-service or budget exhaustion on AI calls?"
**Answer**:
> *"We implemented a sliding-window rate limiter on the `/api/ai/*` route family, capping queries at 10 requests per minute per user or IP address. Furthermore, the summarizer and RAG prompts enforce maximum token ceilings and low temperatures (0.2 - 0.3) to prevent runaway completion generation and unpredictable API billing."*

---

### Q5: "What was your rationale for choosing Prisma ORM over raw SQL queries?"
**Answer**:
> *"Prisma gives us compile-time type safety, automated migration management, and declarative relational integrity (e.g. cascading deletes across User, Profile, Posts, and Conversations). However, as demonstrated in Project 11, we also wrote raw PostgreSQL DDL schemas (`schema.sql`) with explicit indexing to verify relational normalization."*
