# Auto-Renewing Your Usage Window

The 5-hour window starts on your **first message** of a new period — not at midnight.

Send an automated `hi` early in the day to align the reset to a useful time:

> 8:30 AM ping → window resets at **1:30 PM** — fresh block right after lunch.

---

## Setup

Add a daily 8:30 AM warmup to your crontab:

```bash
(crontab -l 2>/dev/null
 echo '30 8 * * * $HOME/.local/bin/claude -p "hi" >> $HOME/.claude-warmup.log 2>&1'
) | crontab -
```

**Verify:**

```bash
crontab -l
cat ~/.claude-warmup.log    # after the first scheduled run
```

For a reset at time `T`, schedule at `T − 5h`.

---

## Caveats

- Workstation must be on and not suspended at trigger time
- If cron's stripped env can't find `node`, wrap as
  `bash -lc '$HOME/.local/bin/claude -p "hi"'`
- Reports indicate windows reset to the exact minute (no top-of-hour bucketing) — confirm via `/usage`
- Remove later:
  ```bash
  crontab -l | grep -v claude-warmup | crontab -
  ```
