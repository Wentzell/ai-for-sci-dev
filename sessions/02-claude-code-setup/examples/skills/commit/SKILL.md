---
name: commit
description: Format staged C++/Python changes with clang-format/ruff and draft a concise commit message. Invoke explicitly with /commit when ready to commit work.
disable-model-invocation: true
---

# Commit Workflow

When invoked, do the following in order:

1. **Inspect the staging area.**
   - Run `git status --short` and `git diff --cached --stat` to see what is staged
   - If nothing is staged, stop and ask the user what to stage

2. **Format the staged files.**
   - For staged `*.cpp` / `*.hpp` / `*.h` / `*.cxx` / `*.hxx` files: run `clang-format -i` on each
   - For staged `*.py` files: run `ruff format` on each (fall back to `black` if `ruff` is unavailable)
   - Re-stage the formatted files (`git add`)

3. **Draft a commit message.**
   - Read the diff (`git diff --cached`)
   - Write a 1-2 line message focused on *why*, not *what* (the diff already says what)
   - Match the existing repo's commit-message style (run `git log --oneline -20` to sample)
   - Show the proposed message to the user; do not commit yet

4. **Wait for confirmation.**
   - The user may edit the message or ask you to commit as-is
   - On confirmation, run `git commit -m "<message>"` (use a heredoc if the message has multiple lines)
   - Do **not** push

## Notes

- Never use `--amend` or `--no-verify` unless the user explicitly asks
- If pre-commit hooks fail, fix the underlying issue and create a *new* commit (not an amend)
- If the diff is large or mixes unrelated changes, suggest splitting before committing
