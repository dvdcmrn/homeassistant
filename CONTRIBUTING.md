# Contributing

## Where changes are merged

All changes are merged on the self-hosted primary Git server; GitHub is a read-only mirror.

- Never merge pull requests on GitHub.
- Contributors who cannot reach the primary push a branch to GitHub, and it is imported and merged on the primary.

## Before you push

- Run [gitleaks](https://github.com/gitleaks/gitleaks) over the commits you are pushing, for example `gitleaks git . --log-opts="origin/main..HEAD"`, or install the hook with `pip install pre-commit && pre-commit install`. Any finding blocks the push.
- Commit with your GitHub noreply author email (`<id>+<username>@users.noreply.github.com`).
- Keep personal info (real names, emails, host names, IP addresses, usernames, passwords) out of code, docs and tests. Use placeholders such as `example.com` or `192.0.2.10`.
