# Security Policy

We take security seriously across Ikenga's projects (including the Ikenga platform — a local-first app that runs an AI engine, executes pkgs, and holds secrets in a vault). We'd rather hear about a problem from you than read about it later — thank you for taking the time to report responsibly.

## Supported versions

As a default across our projects, we provide security fixes for the **latest released version** on the default branch. Older versions are not patched in place — upgrade to the latest release to receive fixes. (Individual repositories may publish a more specific support window in their own `SECURITY.md`.)

| Version | Supported |
|---------|-----------|
| Latest release | ✅ |
| Older releases | ❌ (upgrade to latest) |

## Reporting a vulnerability

**Please do not report security vulnerabilities through public GitHub issues, pull requests, or discussions.**

Use one of these private channels instead:

1. **GitHub Private Vulnerability Reporting (preferred).** Go to the **Security** tab of the affected repository → **Report a vulnerability**. This opens a private advisory visible only to you and the maintainers, with a built-in space to collaborate on a fix and coordinate disclosure.
2. **Email.** If you can't use GitHub's reporting, email `hello@royalti.io`. Encrypt if you can; ask for a key in your first message if needed.

Please include:

- The affected repo and version (or commit).
- A description of the issue and its impact.
- Steps to reproduce, a proof-of-concept, or affected source paths.
- Your platform/OS and the engine adapter in use, if relevant.

## What to expect

- **Acknowledgement within 3 business days** of your report.
- **An initial assessment within 7 business days**, including whether we've confirmed the issue and a rough remediation timeline.
- We'll keep you updated as we work on a fix, and we'll let you know when it ships.

## Coordinated disclosure

We follow coordinated disclosure. We ask that you give us a reasonable window to investigate and ship a fix before any public disclosure — **90 days** from your report, or sooner once a fix is released, whichever comes first. We'll work with you on timing if a fix needs longer.

When a fix ships, we'll publish a security advisory crediting you (unless you'd prefer to remain anonymous — just say so). We don't currently run a paid bug-bounty program, but we genuinely appreciate every good-faith report and will recognize your contribution publicly.

## Scope

This policy is the default for repositories under [`github.com/ikenga-hq`](https://github.com/ikenga-hq) — including the Ikenga platform (the shell, the CLIs `ikenga`/`iyke`, the contract/tokens libraries, and first-party pkgs in `ikenga-pkgs`) and Royalti's other services. A repository that ships its own `SECURITY.md` overrides this default for that repo. Third-party pkgs you install are outside this policy; report those to their authors. If you're unsure whether something is in scope, report it privately and we'll route it.
