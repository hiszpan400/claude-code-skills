---
name: gortex-cross-repo-usage
description: "Find who uses a symbol across all consumer repos."
---
# Find Cross-Repository Usage with Gortex

1. Confirm tracked repositories with `workspace({operation: "repos"})`.
2. Resolve the provider symbol with `search({operation: "symbols", query: "<name>", options: {repo: "<provider>"}})`.
3. Call `relations({operation: "usages", target: {symbol: "<id>"}})` and group results by repository.
4. Add `analyze({kind: "cross_repo", options: {repo: "<provider>"}})` for repository boundaries and `analyze({kind: "contracts", options: {action: "bridge", mode: "impact", symbol: "<id>"}})` for wire-level consumers.
5. Report indexed coverage and name any untracked repositories as an explicit gap.

## Required behavior

- Native Gortex MCP is mandatory for this MCP-configured workflow. If its callable tools are missing, report a Gortex MCP integration failure and stop; do not start a daemon or switch to a CLI/shell fallback.
- Do not substitute shell reads, file search, or Git plumbing.
- Start task-shaped work with `explore`. For one already-known symbol, start with `search`.
- Use `change` before a mutation and again after it. Write only through `edit` or `refactor`.
- Call `capabilities({domain: "<tool>", operation: "<operation>", detail: "schema"})` only when an operation's exact arguments are unclear.
- Report graph-backed paths and symbol IDs. Never invent a result when an operation returns no match.
