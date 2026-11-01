---
name: gortex-debug
description: "Debug a bug, trace an error, or find why something fails."
---
# Debug with Gortex

1. Localize the exact symptom with `explore({operation: "task", task: "<error and observed behavior>"})`.
2. For a literal error, call `search({operation: "text", query: "<exact text>"})`. For a name, use operation `symbols`.
3. Walk toward the cause with `relations({operation: "callers", target: {symbol: "<id>"}})` and `trace({operation: "call_chain", target: {symbol: "<id>"}})`. Use `flow` or `taint` only after resolving both `target` and `to` endpoints.
4. Confirm repository-wide error propagation with `analyze({kind: "error_surface"})`; use `options.repo` to narrow a multi-repository workspace.
5. Before fixing, run `change({operation: "impact", source: {symbols: ["<id>"]}})`. After fixing, run `change` operations `detect`, `tests`, and `guards`.

## Required behavior

- Native Gortex MCP is mandatory for this MCP-configured workflow. If its callable tools are missing, report a Gortex MCP integration failure and stop; do not start a daemon or switch to a CLI/shell fallback.
- Do not substitute shell reads, file search, or Git plumbing.
- Start task-shaped work with `explore`. For one already-known symbol, start with `search`.
- Use `change` before a mutation and again after it. Write only through `edit` or `refactor`.
- Call `capabilities({domain: "<tool>", operation: "<operation>", detail: "schema"})` only when an operation's exact arguments are unclear.
- Report graph-backed paths and symbol IDs. Never invent a result when an operation returns no match.
