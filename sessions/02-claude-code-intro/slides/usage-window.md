# Niche Tip — Auto-Renewing Your Usage Window

The 5-hour window starts on your **first message** — not at midnight. Cron a daily `hi` to align the reset to a useful time.

```bash
30 8 * * * $HOME/.local/bin/claude -p "hi" >> $HOME/.claude-warmup.log 2>&1
```

> 8:30 AM ping → fresh block at **1:30 PM**, right after lunch.

**Anyone here have other tweaks worth sharing?**

Note:
Setup: pipe through `(crontab -l 2>/dev/null; echo '<line>') | crontab -`. Verify with `crontab -l` and `cat ~/.claude-warmup.log` after the first run. For a reset at time T, schedule at T − 5h. Caveats: workstation must be awake at trigger time; if cron's stripped env can't find `node`, wrap as `bash -lc '$HOME/.local/bin/claude -p "hi"'`. Reports indicate windows reset to the exact minute (no top-of-hour bucketing) — confirm via `/usage`. Remove later with `crontab -l | grep -v claude-warmup | crontab -`.
