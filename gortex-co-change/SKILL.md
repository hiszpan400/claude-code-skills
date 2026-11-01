---
name: gortex-co-change
description: "Find what changes together and hidden coupling."
---
# Analyze Co-Change with Gortex

1. Resolve the anchor with `search({operation: "symbols", query: "<name>"})`.
2. Call symbol-scoped `analyze({kind: "co_change", target: {symbol: "<id>"}})` and repository-wide `analyze({kind: "churn"})`.
3. Compare structural coupling through `relations` operations `cluster` and `dependents`.
4. Report strong historical pairs, graph-confirmed dependencies, likely hidden coupling, and an actionable boundary or guard.

## Required behavior

- Native Gortex MCP is mandatory for this MCP-configured workflow. If its callable tools are missing, report a Gortex MCP integration failure and stop; do not start a daemon or switch to a CLI/shell fallback.
- Do not substitute shell reads, file search, or Git plumbing.
- Start task-shaped work with `explore`. For one already-known symbol, start with `search`.
- Use `change` before a mutation and again after it. Write only through `edit` or `refactor`.
- Call `capabilities({domain: "<tool>", operation: "<operation>", detail: "schema"})` only when an operation's exact arguments are unclear.
- Report graph-backed paths and symbol IDs. Never invent a result when an operation returns no match.
