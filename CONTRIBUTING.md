# Contributing to Ikenga

Thanks for considering a contribution. Ikenga is the open-source desktop home for your Claude Code setup — a local-first visual cockpit and package manager for your agents, skills, commands, and MCP servers. It's Apache-2.0 and built in the open — issues, pull requests, and discussion all happen on GitHub. This guide is the org-wide baseline; a few repos add their own `CONTRIBUTING.md` for repo-specific setup, and the [shell](https://github.com/ikenga-hq/ikenga) has the fullest local-dev walkthrough.

If anything here is unclear or out of date, that's a bug too. Open an issue.

## Before you start

- Read the [Code of Conduct](./CODE_OF_CONDUCT.md). It applies everywhere in the project.
- For anything security-related, **do not open a public issue** — follow [SECURITY.md](./SECURITY.md) instead.
- Small fixes (typos, broken links, obvious bugs) — just open a PR. For anything larger, open an issue first so we can agree on the approach before you spend time on it.
- The easiest way to extend Ikenga is to build a **package** — you don't need to touch the platform internals. See [Building a pkg](https://ikenga.dev/docs/build-a-pkg).

## Repository layout

Ikenga is a multi-repo project under [`github.com/ikenga-hq`](https://github.com/ikenga-hq). Pick the repo that owns the thing you're changing:

| Repo | Role | Package manager |
|------|------|-----------------|
| `ikenga` | Tauri 2 + Vite + React 19 desktop app + pkg kernel (the shell) | **bun** |
| `ikenga-contract` | Shared TS package: manifest schema (Zod), RPC types, Engine interface, capability scopes | **pnpm** |
| `ikenga-tokens` | Canonical design tokens (CSS + TS) | **pnpm** |
| `ikenga-cli` | `ikenga` — disk-side pkg manager (`add \| update \| list \| dev`), bun-compiled binary | **bun** |
| `iyke-cli` | `iyke` — Rust runtime controller for a running shell | **cargo** |
| `ikenga-pkgs` | Canonical monorepo for all pkgs (engines, MCP servers, apps, skills) | **pnpm** + Changesets |
| `ikenga-registry` | Static JSON registry of published pkgs | — |
| `ikenga-site` | Marketing site + docs for ikenga.dev | **pnpm** |
| `ikenga-artifact-builder` | Claude Code skill — `npx skills add ikenga-hq/ikenga-artifact-builder` for self-contained HTML artifacts | **pnpm** |

> **Package managers vary by repo. This is deliberate — don't introduce a foreign lockfile.** The shell and the `ikenga` CLI use **bun**; the shared libraries (`contract`, `tokens`) and `ikenga-pkgs` use **pnpm**; `iyke-cli` uses **cargo**.

## Local setup

You'll generally need a recent [Bun](https://bun.sh), [Node](https://nodejs.org), [pnpm](https://pnpm.io), and — for the shell and `iyke-cli` — the [Rust toolchain](https://rustup.rs) and Tauri's [platform prerequisites](https://tauri.app/start/prerequisites/).

**Each repo documents its own dev loop in its `README.md` (and `CLAUDE.md` where present).** As a rule: install with the repo's package manager, then run its dev/build script — e.g. `bun install && bun run tauri dev` for the shell, `pnpm install && pnpm build` for the shared libraries, `cargo build --release` for `iyke-cli`. Libraries publish through `workspace:*` links during cross-package dev: rebuild the dependency, and the consumer picks it up on next reload.

If you're authoring a **package** rather than changing the platform, use `ikenga dev <path>` to hot-mount it into a running shell (watches the manifest and reload globs; `Ctrl-C` unregisters cleanly). Per-archetype authoring guides live in the shell repo's `docs/pkg-patterns/`, with copyable scaffolds in `docs/pkg-patterns/_templates/`.

## Filing issues

Use the templates — they exist so we can act on a report without a round-trip for missing detail.

- **Bug reports** — include your OS, Ikenga version, and the smallest reproduction you can manage. See the bug template.
- **Feature requests** — describe the problem before the solution. See the feature template.
- **Security issues** — do **not** use public issues. See [SECURITY.md](./SECURITY.md).
- **Questions / ideas** — open a GitHub Discussion rather than an issue.

One report per issue. If you've found three bugs, file three issues.

## Branch, commit, and PR workflow

1. **Fork** the repo and create a branch off `main`. Name it for the work — `fix/iframe-handshake-race`, `feat/codex-adapter`, `docs/contributing-setup`.
2. **Commit** in logical units. We follow [Conventional Commits](https://www.conventionalcommits.org/): `type(scope): summary`, e.g. `fix(kernel): unregister dev pkg on Ctrl-C`. Common types: `feat`, `fix`, `docs`, `refactor`, `test`, `chore`. Repos that publish through Changesets (`ikenga-contract`, `ikenga-tokens`, `ikenga-cli`, `ikenga-pkgs`, `ikenga-artifact-builder`) also expect a changeset (`pnpm changeset`) for any user-facing change.
3. **Keep PRs focused.** One concern per PR. If it grew two unrelated changes, split it.
4. **Open the PR against `main`**, fill in the PR template, and link the issue it closes (`Closes #123`).
5. A maintainer will review. Expect questions — review is a conversation, not a gate. Push follow-up commits to the same branch; we squash on merge unless the history is worth keeping.

## Tests and standards

- Run the test suite for the repo you touched before opening a PR (`cargo test`, `node --test`, package scripts — see the repo's README/`CLAUDE.md`).
- Match the existing style; don't reformat unrelated code in the same PR. Each repo's formatter/linter config is authoritative.
- Add or update tests for behavior you change. A bug fix should come with a test that would have caught it.
- Don't introduce a foreign package manager or lockfile (see the table above).

## Licensing and your contributions

Ikenga's platform code and packages are **Apache-2.0**. We use **inbound = outbound**: by opening a pull request, you agree that your contribution is licensed under the same Apache-2.0 terms as the project. We do **not** require a CLA.

Why: an Apache-2.0 *license* does not by itself require a CLA — that's a foundation *governance* requirement, not a license one. Ikenga is Apache-2.0-licensed but is not an ASF project, so we keep contribution friction low the way most non-foundation OSS projects do.

## Getting help

- Project docs: [ikenga.dev](https://ikenga.dev) (in-site docs, including the [contributing guide](https://ikenga.dev/docs/contributing)).
- GitHub Discussions for questions and design conversation.
- Be patient and specific — the more reproducible your report, the faster we can help.

Welcome aboard.
