# harshitgadge.github.io: the booth

**Live:** https://harshitgadge.github.io

My projects as records on a turntable. Pick one from the crate and it goes on the deck: its liner notes show what it does, the number that backs it up, and the stack.

- **Every record plays a song.** Each record is paired with one of seven songs I build to, and putting it on plays that song through one official Spotify player (Spotify's iFrame API, started by the visitor's click). A sound switch turns it off and is remembered; a deep link loads the song without playing it; nothing from Spotify loads until a record is on the deck. If the API can't load, the page falls back to the plain Spotify player. No audio is hosted here.
- **Every record takes questions.** Once a record is on, an ask box opens for that project. The question goes to my [agentic-rag-service](https://github.com/HarshitGadge/agentic-rag-service), deployed read-only on Render, with `source_filter` set to the repo name, so retrieval only searches that project's docs. A record whose docs aren't indexed yet says so and takes no questions.
- **Cited, not generated.** The public service runs in extractive mode: each line of the answer is a sentence lifted from a retrieved passage, with a badge linking to its source file on GitHub.
- **Real timings.** The five-stage strip (plan, embed, search, rank, answer) shows the per-stage milliseconds the service measured for that request.
- **Cold starts.** The service runs on a free instance that sleeps when idle. The page pings `/stats` on load and says when the server is waking up.

It works on a phone and in light mode, and deep-links to a record with `#<repo-name>`. The old `/booth/` address redirects here, keeping the record in the link.

One file, no build step, no dependencies. To point it at a local copy of the service, use `?api=http://localhost:8000` (the service must list the page's origin in `RAG_CORS_ORIGINS`).
