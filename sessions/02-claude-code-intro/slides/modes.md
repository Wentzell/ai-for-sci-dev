# The Modes

<div class="two-col">
<div>

**Default**
- Asks before every write/edit/non-allowlisted bash
- Safe starting state

**`acceptEdits`**
- Runs through the permissions allowlist without asking
- File Edits get automatically approved

</div>
<div>

**Plan mode**
- Read-only investigation, then a plan
- Iterate & Approve before any change
- *The mode for scientific software work*

**`auto`**
- Continuous execution with monitoring agent
- For unattended runs after a plan is approved

</div>
</div>

**`Shift+Tab` cycles** `default → acceptEdits → plan → auto`

Note:
Concrete example to mention live: the DLR validity rule in my CLAUDE.md catches Claude trying to apply DLR operations to error bars or other non-spectral quantities. Plan mode surfaces the misapplication before any edit is made. `dontAsk` and `bypassPermissions` exist outside the cycle — pick via the mode selector when you need them. If time allows, show plan mode live on a TRIQS repo: small concrete ask → `Shift+Tab` into plan → watch it explore → read the produced plan → approve.
