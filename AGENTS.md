# Agents

## Git workflow: Gitea only

- **Never merge on GitHub.** GitHub (github.com/dvdcmrn/homeassistant) is a read-only mirror.
- All merges happen on Gitea (git.valhal.uk) through Loki. Gitea `main` is the source of truth.
- Cloud agents that can't reach Gitea push a branch to GitHub (never `main`, never merge a PR); Loki imports it into Gitea and merges there.

This repository has **no local AI toolkit** (no `.cursor/` agent trees, no `.claude/`, no `CLAUDE.md`).

Homelab knowledge and ops tools are provided through MCP servers configured in the Cursor project, not in this repo. Apart from the Gitea host above, host names, addresses and credentials are never stored here.

## Repository rules

- Run `gitleaks git --log-opts="<range>"` (or `pre-commit run --all-files`) before every push and before opening a PR. A finding blocks the push.
- Commit author email must be the GitHub noreply address.
- No personal info (real names, emails, host names, IPs, usernames, passwords) in code, docs or tests. Use placeholders such as `example.com` or `192.0.2.10`.

## Skills / rules

Workflow skills live in Cursor (`~/.cursor/skills`), not in this repo.
