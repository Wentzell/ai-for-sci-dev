# Skills

A **skill** is a reusable bundle of instructions that extends Claude with a named capability. Invoke with `/<skill-name>`.

**Same two scopes** as settings: `~/.claude/skills/<name>/` *or* `<repo>/.claude/skills/<name>/`

```yaml
---
description: Distill session learnings into memory files
effort: medium
---

Distill durable lessons from this session into the appropriate
persistent file:

1. **Gather** — read user-level & repo-level CLAUDE.md, scan
   project memory to avoid duplicates
2. **Analyze** — review the conversation for corrections,
   non-obvious discoveries, design decisions worth preserving
3. **Review & apply** — propose each addition diff-style;
   write only what I approve
```

`/debrief` then captures the session's lessons everywhere they belong.

Note:
Required frontmatter: `description` (what the model reads when deciding whether to auto-trigger). Optional: `effort`, `disable-model-invocation: true` (strictly user-invoked — good for anything with side effects). Body supports `$ARGUMENTS`, `` ! `cmd` `` for shell output, and `@path` for file includes. Skills can ship templates / scripts / reference docs in the same directory.

---

## Have you built a skill?

**What for? What worked, what didn't?**

Real skills I use: `/api-review`, `/jenkins`, `/optimize`, `/profile`, `/tidy-commits` — domain-specific TRIQS workflows.

Want to dig deeper? `/powerup` → *Automate your workflow* & *Multiply yourself*.

Note:
If no one has built one yet, walk through the take-home `/debrief` example live. Adjacent concepts to mention if asked: hooks (shell triggers on events configured in settings.json) and subagents (`/agents`).
