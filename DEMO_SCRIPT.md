# Capstone Live Demo Walkthrough Script

**Emganwini Nedbank Hub | Master Project Portfolio**  
*Summative 3 Presentation Demo Script*

---

## ⏱️ Step-by-Step 10-Minute Presentation Script

### Act 1: User Onboarding & Authentication (Minutes 00:00 - 02:00)
- **Presenter**: *"Welcome, evaluators. I begin by accessing our live production deployment on Vercel."*
- **Action**: Navigate to `/signup`. Register a test client account (`thabo.demo@nedbankhub.co.za`).
- **Technical Highlight**: Password hashed with salted bcrypt (10 rounds). JWT token generated and saved in browser storage. Instant redirect to `/dashboard`.
- **Action**: Demonstrate log out, then log back in via `/login`. Notice how navigation dynamically swaps between guest buttons and active user avatar.

### Act 2: Financial Advisory Feed & Full CRUD (Minutes 02:00 - 04:30)
- **Presenter**: *"Clients need timely guidance. Here on the Dashboard, we display active articles from advisors."*
- **Action**: Click `+ New Guidance Post`. Enter title *"2026 FLISP First-Time Homebuyer Threshold Updates"* and content details.
- **Technical Highlight**: Trigger `POST /api/posts`. Post instantly renders on top of the list without needing a full page reload.
- **Action**: Click `Edit` on the created post, change the title to include *"Official Update"*, and save. Verify `PUT /api/posts/:id` persists changes.
- **Action**: Click `Delete`, review the modal warning in `DeleteConfirmation`, and delete. Verify `DELETE /api/posts/:id` removes it with `204 No Content`.

### Act 3: NedPulse Copilot & RAG Semantic Search (Minutes 04:30 - 07:30)
- **Presenter**: *"Now we arrive at our core innovation: NedPulse AI Copilot."*
- **Action**: Switch to the `💬 Conversational Copilot` tab. Type: *"What is the difference between a 32-day notice deposit and a fixed deposit?"*
- **Technical Highlight**: Observe animated thinking indicator. Receive contextual multi-turn response citing Nedbank product advantages.
- **Action**: Switch to the `🔍 Grounded RAG Search` tab. Type: *"What is the minimum opening deposit for the notice flexi account?"*
- **Technical Highlight**: Vector search against the 2,500-word knowledge base returns the exact clause, stating `R1,000` with citation `[Source 1]` and source chunk snippets.
- **Action**: Ask an out-of-scope question: *"Who won the 1995 Rugby World Cup?"*
- **Technical Highlight**: Guardrail triggers: *"I do not have sufficient information in the verified Nedbank knowledge base to answer this question."* Zero hallucinations.

### Act 4: Document Summarization & Consultation History (Minutes 07:30 - 09:00)
- **Presenter**: *"Clients often receive lengthy 10-page disclosures. Our 3-sentence summarizer solves this."*
- **Action**: Switch to `⚡ 3-Sentence Summarizer`. Paste a complex legal loan disclosure paragraph.
- **Technical Highlight**: Generates exactly 3 concise, grammatically verified sentences with token metrics and estimated cost breakdown.
- **Action**: Open the Conversation History drawer. Show previous sessions stored in PostgreSQL. Click a past inquiry and resume the session smoothly.

### Act 5: Wrap-up & Transition to Q&A (Minutes 09:00 - 10:00)
- **Presenter**: *"In conclusion, Nedbank SmartFin is fully deployed, secure, POPIA compliant, and solves real operational pain points. I now welcome questions from the review committee."*
