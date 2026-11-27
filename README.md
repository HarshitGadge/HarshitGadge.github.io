# harshitgadge.github.io: ask my portfolio

**Live:** https://harshitgadge.github.io

A single static page that talks to my [agentic-rag-service](https://github.com/HarshitGadge/agentic-rag-service), deployed read-only on Render. The service has indexed the READMEs and design notes of five of my projects.

- **Every dot is a passage.** The background draws one dot per indexed chunk, grouped by project. The counts come from the live `/stats` endpoint. When an answer comes back, the passages it cites light up and beam into the answer card. A passage always lights the same dot, because the dot is chosen by hashing its chunk id.
- **Real timings.** The five-stage strip (plan, embed, search, rank, answer) shows the per-stage milliseconds the service measured for that request.
- **Cited, not generated.** The public service runs in extractive mode: each line of the answer is a sentence lifted from a retrieved passage, with a badge linking to its source file on GitHub.
- **Cold starts.** The service runs on a free instance that sleeps when idle. The page pings `/stats` on load and tells you when the server is waking up.

**The booth** (`/booth/`): my projects as records on a turntable. Pick one from the crate and its liner notes show what it does, the number that backs it up, and the stack. It's silent, works on a phone, and deep-links to a record with `#<repo-name>`.

One file per page, no build step, no dependencies. To point it at a local copy of the service, use `?api=http://localhost:8000` (the service must list the page's origin in `RAG_CORS_ORIGINS`).

<sub>For engineers: ↑ ↑ ↓ ↓ ← → ← → b a</sub>
