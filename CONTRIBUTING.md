# Contributing

## Workflow

This project has a single developer and works directly on `main` on the self-hosted primary Git server.

- Commit and push straight to `main` on the primary. No branches, no pull requests and no extra tags.
- CI on the primary builds, tests and scans every push to `main`.
- Only after CI passes is `main` pushed on to GitHub. GitHub is a read-only mirror; nothing is committed or merged there.

## Before you push

- Run [gitleaks](https://github.com/gitleaks/gitleaks) over the commits you are pushing, for example `gitleaks git . --log-opts="origin/main..HEAD"`, or install the hook with `pip install pre-commit && pre-commit install`. Any finding blocks the push, and the same gitleaks gate runs again before anything reaches GitHub.
- Commit with a GitHub noreply author email (`<id>+<username>@users.noreply.github.com`).
- No secrets, keys or personal info (real names, emails, host names, IP addresses, usernames, passwords) in code, docs or tests. Use placeholders such as `example.com` or `192.0.2.10`.
