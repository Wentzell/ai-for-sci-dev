# Installing Claude Code

**Recommended:** native installer

```bash
curl -fsSL https://claude.ai/install.sh | bash
```

- No node needed · auto-updates on the `latest` channel
- Install once on NFS home (`/mnt/home/<user>`) — follows you to all nodes
- `claude update` to update manually

On first launch, run `/login` and pick **Claude Team** (your Flatiron seat).

---

## Other paths

- **macOS:** `brew install --cask claude-code` *(needs `brew upgrade` for updates)*
- **npm:** `npm install -g @anthropic-ai/claude-code` *(also published, but native is primary)*

*Other login options exist (Anthropic Console API key, Bedrock / Vertex / Foundry) — not needed at Flatiron.*

---

## Try it now

```bash
cd /tmp && claude
```

1. Log in if it's your first time
2. Type something — `hi`
3. `/exit`

Note:
Buffer ~1 minute here for stragglers. If anyone hits node-version or NFS-quota issues with npm/Homebrew, point them at the curl installer.
