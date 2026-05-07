# Settings — User & Project Scope

<div class="two-col">
<div>

**User** — `~/.claude/`
Your defaults, follows you everywhere

</div>
<div>

**Project** — `<repo>/.claude/`
Checked in, shared with collaborators

</div>
</div>

Same split for **`settings.json`**, **`CLAUDE.md`** *&* **`skills/`** — learn it once.

```json
{
  "model": "claude-opus-4-7",
  "theme": "dark-ansi",
  "effortLevel": "high",
  "env": {
    "CMAKE_EXPORT_COMPILE_COMMANDS": "ON"
  },
  "permissions": {
    "allow": ["Read", "Bash(cmake *)", "Bash(ctest *)", "Bash(ninja *)"],
    "deny":  ["Edit(~/.ssh/**)", "Edit(**/.env*)"]
  }
}
```

Full sample: see `~/.claude/settings.json` · permissions evaluate **deny → ask → allow**.

Note:
Settings precedence high→low: managed (org) · CLI flags · `.claude/settings.local.json` (gitignored) · `.claude/settings.json` · `~/.claude/settings.json`. Auto-compaction window is set via `CLAUDE_CODE_AUTO_COMPACT_WINDOW` env var, not a settings key. Bare-metal HPC nodes typically need `sandbox` disabled. Sonnet 4.6 for everyday work, Opus 4.7 for harder reasoning — toggle mid-session with `/model`.

---

## `CLAUDE.md` — Persistent Instructions

*Anything you'd otherwise re-explain every session.*

<div class="two-col">
<div>

**Three tiers**
- **Global** `~/.claude/CLAUDE.md`
- **Project** `<repo>/CLAUDE.md`
- **Subdir** `CLAUDE.md` *(on-demand)*

Bootstrap with **`/init`** — drafts a starter from the repo.

</div>
<div>

**What belongs there**

Anything specific to your workflow or domain knowledge — e.g.
- Build invocation: `cmake` / `ninja` / `ctest`
- Test-reference workflow
- Domain rules (DLR is spectral-only)

</div>
</div>

**Anyone want to share what's in theirs?**
