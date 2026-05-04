# Take-Home Examples

Generic starter files for Claude Code on the Flatiron HPC. Copy, adapt, commit.

## What's here

| File | Install to | Purpose |
|---|---|---|
| `settings.json` | `~/.claude/settings.json` | User-level defaults — model, env, permissions, attribution |
| `CLAUDE.global.md` | `~/.claude/CLAUDE.md` | Persistent instructions for *every* session — your dev environment |
| `CLAUDE.project.md` | `<your-repo>/CLAUDE.md` | Per-repo instructions — build, test, conventions |
| `skills/commit/` | `~/.claude/skills/commit/` | Example user-invoked skill — clang-format + draft commit message |

## Quick install

```bash
# user-level settings + global CLAUDE.md + commit skill
mkdir -p ~/.claude/skills
cp settings.json   ~/.claude/settings.json
cp CLAUDE.global.md ~/.claude/CLAUDE.md
cp -r skills/commit ~/.claude/skills/

# project-level CLAUDE.md (run inside the target repo)
cp CLAUDE.project.md /path/to/repo/CLAUDE.md
```

If you already have any of these files, **don't blindly overwrite** — diff first:

```bash
diff -u ~/.claude/settings.json settings.json
```

## Reminders

- **Settings precedence** (highest → lowest): managed → CLI → `.claude/settings.local.json` → `.claude/settings.json` → `~/.claude/settings.json`
- **`.claude/settings.local.json`** is gitignored — use it for per-checkout overrides
- **`CLAUDE.md`** in a subdirectory loads on demand when Claude reads files there
- **Skills** require YAML frontmatter with at minimum `name` and `description`

## Where to go next

- Slash command tour: `/help`, `/status`, `/config`, `/context`, `/usage`, `/model`, `/effort`, `/memory`, `/permissions`, `/powerup`
- Plan mode: `Shift+Tab` cycles `default → acceptEdits → plan`
- Mid-session navigation: `Esc` (interrupt), `Esc Esc` (rewind), `/resume`, `/fork`, `/rename`
