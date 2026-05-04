# Skills

A **skill** is a reusable bundle of instructions that extends Claude with a named capability. Invoke with `/<skill-name>`.

**Two scopes** — same pattern as settings & `CLAUDE.md`

- **User-level**: `~/.claude/skills/<name>/SKILL.md` — available everywhere
- **Project-level**: `<repo>/.claude/skills/<name>/SKILL.md` — checked into the repo

**Layout**: a directory containing `SKILL.md` plus any optional templates / scripts / reference docs.

**Required YAML frontmatter:** `name`, `description`. The description is what the model reads when deciding whether the skill is relevant — phrase it as *what it's for and when to use it*, not just a label.

---

## Two Ways a Skill Activates

- **User invokes** by typing `/<name>` — always works
- **Model auto-discovers** when your request matches the description
  - Set `disable-model-invocation: true` for strict user-only triggering (anything with side effects)

---

## A Worked Example — `/commit`

```yaml
---
name: commit
description: Run clang-format on staged C++/Python and draft a commit message
disable-model-invocation: true
---

1. Run clang-format on staged files
2. Show me the diff
3. Propose a one-line commit message
```

`cp -r examples/skills/commit ~/.claude/skills/` → `/commit` is live in every session.

The body supports `$ARGUMENTS` (user input), `` ! `cmd` `` (shell output fed to the model), and `@path` (file include).

---

## When to Choose What

- **Auto-trigger when relevant** → normal frontmatter
- **User-only, side effects** *(deploy, push, send msg)* → `disable-model-invocation: true`
- **Need supporting files** *(templates, reference docs)* → ship them in the skill directory; reference from `SKILL.md`

Inspiration *(real skills I use)*: `/api-review`, `/jenkins`, `/optimize`, `/profile`, `/tidy-commits` — domain-specific TRIQS workflows are exactly what skills are built for.

---

## Adjacent Concepts

- **Hooks** — shell triggers on events (`Stop`, `PreToolUse`, ...) configured under `hooks` in `settings.json`. *(I use one for a tmux status indicator.)*
- **Subagents** — parallel/isolated agents — `/agents`

`/powerup` → *Automate your workflow* & *Multiply yourself* cover the same ground.
