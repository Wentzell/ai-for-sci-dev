# Starting & Resuming Sessions

From the shell:

- `claude` — new session in the current directory
- `claude -c` / `--continue` — most recent session for *this* directory
- `claude -r` / `--resume` — interactive picker across past sessions
- `claude -p "..."` / `--print` — one-shot, non-interactive (great for scripts & pipes)

Sessions are **per working directory**, stored under
`~/.claude/projects/<slug-of-cwd>/`

---

## Try it now

1. `claude` in a scratch dir → say `hi` → `/exit`
2. `claude -c` → watch the previous context come back

---

# Mid-session navigation

<div class="two-col">
<div>

**Stop the assistant**
- `Esc` — interrupt mid-response or mid-tool-call
- First reflex when something heads the wrong way

**Undo a direction**
- `Esc Esc` (or `/rewind`) — picker over previous turns; everything after is dropped
- Use when you regret a path and want a clean redo

</div>
<div>

**Switch / branch**
- `/resume` — session picker from *inside* Claude
- `/fork` — branch off current state into a new session
- `/rename` — give the session a memorable name (findable later)

**Reset hard**
- `/clear` — drop history, keep the session
- Blunt instrument; reach for `/rewind` first

</div>
</div>

---

## Try it now — `Esc Esc`

1. Ask Claude something trivial
2. Press `Esc Esc`
3. Pick a turn — watch the context shrink

Note:
`Esc` (single) is muscle memory worth building — most "oh no, stop" moments are solved by it. The `Undo anything` `/powerup` lesson goes deeper into rewind.
