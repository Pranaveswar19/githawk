# GitHawk

Internal tool for tracking GitHub issues and commit history, with an AI assistant that understands your repository.

---

## Stack

| Layer      | Technology                     | Why                                          |
| ---------- | ------------------------------ | -------------------------------------------- |
| Frontend   | HTML + Tailwind + Vanilla JS   | No build step, fast to iterate               |
| Backend    | Node.js + Express              | Non-blocking, same language as frontend      |
| Database   | Supabase (Postgres + pgvector) | Managed Postgres with built-in vector search |
| Embeddings | OpenAI text-embedding-3-small  | Fast, cheap, high quality                    |
| Chat       | Groq (Llama 3)                 | Fast inference, generous free tier           |
| Deployment | Railway                        | Auto-deploys from GitHub on every push       |

---

## Structure

```
githawk/
├── frontend/
│   └── index.html
├── backend/
│   ├── server.js
│   ├── package.json
│   ├── .env.example
│   ├── routes/
│   │   ├── sync.js
│   │   ├── issues.js
│   │   └── commits.js
│   ├── services/
│   │   ├── github.service.js
│   │   ├── db.service.js
│   │   └── rag.service.js
│   ├── middleware/
│   │   ├── rateLimit.js
│   │   └── errorHandler.js
│   └── db/
│       └── schema.sql
├── .gitignore
└── README.md
```

---

## The one rule

```
routes → services → database
```

Routes handle HTTP only. Services handle logic. Nothing crosses that boundary.

---

## Phases

- **Phase 1** — Frontend shell ✓
- **Phase 2** — GitHub sync, Supabase storage, embeddings on write
- **Phase 3** — AI chatbot wired end to end

---

## Running locally

```bash
cd backend
npm install
node server.js
```

Open `frontend/index.html` directly in your browser.

## Environment

Variables are stored in `.env` at the project root. See phase 2 for the full list.

```

```
