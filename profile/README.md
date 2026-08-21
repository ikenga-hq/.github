# Ikenga

**The open-source desktop home for your Claude Code setup** — a local-first visual cockpit and package manager for your agents, skills, commands, and MCP servers. Apache-2.0, built in the open.

→ **[ikenga.dev](https://ikenga.dev)** · [Download](https://ikenga.dev) · [Docs](https://ikenga.dev/docs) · [Contributing](https://ikenga.dev/docs/contributing)

## The repos

| Repo | Role | Package manager |
|------|------|-----------------|
| [`ikenga`](https://github.com/ikenga-hq/ikenga) | Tauri 2 + Vite + React 19 desktop app + pkg kernel (the shell) | bun |
| [`ikenga-contract`](https://github.com/ikenga-hq/ikenga-contract) | Shared TS package: manifest schema (Zod), RPC types, Engine interface, capability scopes | pnpm |
| [`ikenga-tokens`](https://github.com/ikenga-hq/ikenga-tokens) | Canonical design tokens (CSS + TS) | pnpm |
| [`ikenga-cli`](https://github.com/ikenga-hq/ikenga-cli) | `ikenga` — disk-side pkg manager (`add \| update \| list \| dev`) | bun |
| [`iyke-cli`](https://github.com/ikenga-hq/iyke-cli) | `iyke` — Rust runtime controller for a running shell | cargo |
| [`ikenga-pkgs`](https://github.com/ikenga-hq/ikenga-pkgs) | Canonical monorepo for all pkgs (engines, MCP servers, apps, skills) | pnpm + Changesets |
| [`ikenga-registry`](https://github.com/ikenga-hq/ikenga-registry) | Static JSON registry of published pkgs | — |
| [`ikenga-site`](https://github.com/ikenga-hq/ikenga-site) | Marketing site + docs for ikenga.dev | pnpm |
| [`ikenga-artifact-builder`](https://github.com/ikenga-hq/ikenga-artifact-builder) | Claude Code skill for self-contained HTML artifacts | pnpm |

## Contributing

We'd love your help — especially building **packages** (the most common way to extend Ikenga). Start with the [contributing guide](https://ikenga.dev/docs/contributing), then read [CONTRIBUTING.md](https://github.com/ikenga-hq/.github/blob/main/CONTRIBUTING.md). Everything here is Apache-2.0; by opening a PR you agree your contribution ships under the same terms (inbound = outbound, no CLA).

Found a security issue? **Don't** open a public issue — see [SECURITY.md](https://github.com/ikenga-hq/.github/blob/main/SECURITY.md).
