# The Modes

<div class="two-col">
<div>

**Default**
- Asks before every write/edit/non-allowlisted bash
- Safe starting state

**`acceptEdits`**
- Runs through the permissions allowlist without asking
- Faster once you trust the direction

</div>
<div>

**Plan mode**
- Read-only investigation
- Produces a plan, requires explicit approval before any change
- The mode for scientific software work

**`auto`**
- Continuous execution — no prompts within the sandbox
- For unattended runs after a plan is approved

</div>
</div>

**`Shift+Tab` cycles** `default → acceptEdits → plan → auto`

*(`dontAsk` and `bypassPermissions` exist outside the cycle — pick via the mode selector.)*

---

## Why Plan Mode Matters for Scientific Code

- **Builds are expensive** — cluster jobs, long TRIQS compiles. Cheap to plan, expensive to redo
- **Sanity-check against domain knowledge** before any edit  *(e.g. "are you actually applying DLR to the right object?")*
- **Forces investigation first** — read existing code, state assumptions before changing anything
- **The plan is the artifact** — reject, edit, or discuss before approving

On approval:

- pick the follow-on mode — `auto` / `acceptEdits` / manual review
- or keep planning with feedback (iterate)

Note:
Concrete example to mention live: the DLR validity rule in my CLAUDE.md catches Claude trying to apply DLR operations to error bars or other non-spectral quantities. Plan mode surfaces the misapplication before any edit is made.

---

## Live demo — plan mode on a TRIQS repo

*(audience watches)*

- Small, concrete ask
- `Shift+Tab` into plan mode
- Watch it explore — point out file paths it picks up
- Read the produced plan
- Approve → manual review (safest for the demo)

Note:
Stopwatch this; biggest timing risk in the talk. If running long, skip the manual-review walkthrough and just show the produced plan + approval prompt.
