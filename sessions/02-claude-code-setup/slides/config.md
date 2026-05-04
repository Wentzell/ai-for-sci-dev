# The Two Scopes You'll Actually Use

<div class="two-col">
<div>

**User scope** — `~/.claude/`

Your defaults, follows you everywhere
- `settings.json`
- `CLAUDE.md`
- `skills/`

</div>
<div>

**Project scope** — `<repo>/.claude/`

Checked into git, shared with collaborators
- `settings.json`
- `CLAUDE.md` *(usually at repo root)*
- `skills/`

</div>
</div>

The same split applies to **settings**, **CLAUDE.md** *&* **skills** — learn it once.

**Settings precedence** (high → low):

1. managed (org)
2. CLI flags
3. `.claude/settings.local.json` *(gitignored)*
4. `.claude/settings.json`
5. `~/.claude/settings.json`

> *settings = how Claude **runs** · CLAUDE.md = what Claude **knows***

---

## A Sane Flatiron Starter `settings.json`

```json
{
  "model": "claude-sonnet-4-6",
  "theme": "dark-ansi",
  "editorMode": "vim",
  "env": {
    "EDITOR": "vim",
    "PYTHONDONTWRITEBYTECODE": "1",
    "CMAKE_EXPORT_COMPILE_COMMANDS": "ON",
    "CMAKE_COLOR_DIAGNOSTICS": "ON"
  },
  "attribution": {
    "commit": "Co-Authored-By: Claude <noreply@anthropic.com>"
  }
}
```

- **Sonnet 4.6** for everyday work — fast, sufficient for most edits/tests/refactors
- **Opus 4.7** for harder reasoning — debugging, architecture, plan mode on unfamiliar repos
- Toggle mid-session with `/model` (aliases `sonnet` / `opus` also work)

Full file: `examples/settings.json` in this session — copy & edit

Note:
Auto-compaction window is set via the env var `CLAUDE_CODE_AUTO_COMPACT_WINDOW`, not a settings key. Mention as an aside if asked. NFS-aware: don't run recursive sweeps from `/mnt/home`.

---

## Permissions & Sandbox

Rules: `Tool` or `Tool(specifier)`. Glob/wildcard supported.
Evaluation: **deny → ask → allow** (first match wins)

```json
"permissions": {
  "allow": [
    "Read", "WebFetch", "WebSearch",
    "Bash(git status)", "Bash(git diff *)",
    "Bash(cmake *)", "Bash(ctest *)", "Bash(ninja *)",
    "Bash(module *)", "Bash(gh pr view *)"
  ],
  "deny": [
    "Edit(~/.ssh/**)", "Edit(**/.env*)", "Read(./.env)"
  ]
}
```

- Pre-authorize what you trust → fewer prompts
- Bare-metal HPC nodes typically need `sandbox` disabled

---

## Try it now

Open `/config` and look at the permissions panel — or open `~/.claude/settings.json` in another pane.

---

## `CLAUDE.md` — Persistent Instructions

**Global** (`~/.claude/CLAUDE.md`) — your dev environment, always loaded
**Project** (`<repo>/CLAUDE.md`) — repo-specific, loaded when working there
**Subdirectory** `CLAUDE.md` — loaded **on-demand** when Claude reads files there

What belongs there:

- Build invocation: `cmake` / `ninja` / `ctest`
- Module-load default, NFS hygiene rules
- Domain rules (e.g. DLR is only valid for spectral quantities)
- Test-reference workflow

> *Anything you'd otherwise re-explain on every session*

Take-home samples: `examples/CLAUDE.global.md` & `examples/CLAUDE.project.md`
