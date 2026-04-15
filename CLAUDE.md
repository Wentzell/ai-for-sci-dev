# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Reveal.js presentation series: "AI for Scientific Software Development" — recurring meetings at CCQ, Flatiron Institute. Slides are viewable via GitHub Pages at https://wentzell.github.io/ai-for-sci-dev/.

## Serving Locally

```bash
python3 -m http.server 3000
```

Then open http://localhost:3000/sessions/01-intro/. An HTTP server is required — `file://` won't load external markdown.

## Architecture

- `index.html` — Root landing page listing all sessions
- `sessions/NN-topic/index.html` — Reveal.js shell for each session, loads reveal.js from unpkg CDN
- `sessions/NN-topic/slides/*.md` — Slide content in markdown per section
- `shared/style.css` — Custom CSS shared across sessions

Reveal.js 6.x is loaded entirely from `https://unpkg.com/reveal.js@6/` — no local dependencies.

## Adding a New Session

1. Copy an existing session directory (e.g. `cp -r sessions/01-intro sessions/02-topic`)
2. Edit the markdown files in `slides/`
3. Update the session's `index.html` title and `<section>` blocks
4. Add a link in the root `index.html`

## Markdown Slide Syntax

- Horizontal slide break: blank line, `---`, blank line
- Vertical slide break: blank line, `----`, blank line
- Speaker notes: `Note:` on its own line
- Code blocks: fenced with language tag (e.g. ` ```cpp `) for syntax highlighting
