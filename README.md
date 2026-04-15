# AI for Scientific Software Development

Slide decks for the recurring CCQ meeting series on using AI agents for scientific software development.

**View online:** https://wentzell.github.io/ai-for-sci-dev/

## Sessions

| # | Topic | Slides |
|---|-------|--------|
| 01 | Introduction | [view](sessions/01-intro/) |

## Adding a New Session

1. Copy an existing session directory: `cp -r sessions/01-intro sessions/02-topic`
2. Edit the markdown files in `sessions/02-topic/slides/`
3. Update `sessions/02-topic/index.html` title and `<section>` blocks as needed
4. Add an entry to the root `index.html` landing page

## Local Development

External markdown slides require an HTTP server (browsers block `file://` fetches):

```bash
python3 -m http.server 3000   # then open http://localhost:3000/sessions/01-intro/
```

Slides use [Reveal.js 6](https://revealjs.com/) loaded from CDN — no install step needed.
