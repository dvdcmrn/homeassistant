# Contributing

## Workflow

This project has a single developer and works directly on `main` on the self-hosted primary Git server.

- Commit and push straight to `main` on the primary. No branches, no pull requests and no extra tags.
- CI on the primary builds, tests and scans every push to `main`.
- Only after CI passes is `main` pushed on to GitHub `main`, with no secrets, keys or personal info. GitHub is a read-only mirror; nothing is committed or merged there.
- Straight after that, the build is deployed so the latest version can be tested, and the owner is told the deployment was updated.

## Deploy

The deploy target is the Home Assistant OS configuration, not a container.

1. Take a backup of the Home Assistant configuration first.
2. Sync the changed files from `main` to the Home Assistant config.
3. Reload only the affected integrations (for example automations, templates or the custom integration) through the Home Assistant API.
4. A full Home Assistant restart is never done automatically; it needs the owner's explicit OK each time.

Docs-only changes are not deployed.

## Before you push

- Run [gitleaks](https://github.com/gitleaks/gitleaks) over the commits you are pushing, for example `gitleaks git . --log-opts="origin/main..HEAD"`, or install the hook with `pip install pre-commit && pre-commit install`. Any finding blocks the push, and the same gitleaks gate runs again before anything reaches GitHub.
- Commit with a GitHub noreply author email (`<id>+<username>@users.noreply.github.com`).
- No secrets, keys or personal info (real names, emails, host names, IP addresses, usernames, passwords) in code, docs or tests. Use placeholders such as `example.com` or `192.0.2.10`.
