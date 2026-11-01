---
name: gortex-incident-investigation
description: "Walk a production symptom back to its root cause."
---
# Investigate an Incident with Gortex

1. Paste the exact symptom into `explore({operation: "task", task: "<alert, error, and time window>"})`.
2. Search exact error text with `search({operation: "text", query: "<literal>"})`.
3. Walk `relations` operation `callers` and `trace` operations `call_chain`, `flow`, or `taint` from symptom toward cause.
4. Correlate repository-wide `analyze({kind: "recent_changes"})` with symbol-scoped `recall({operation: "surface", arguments: {symbol_ids: "<id>", task: "<symptom>"}})`.
5. Separate evidence, hypothesis, and unknowns. Gate any fix through `change` before and after the mutation.

## Required behavior

- Native Gortex MCP is mandatory for this MCP-configured workflow. If its callable tools are missing, report a Gortex MCP integration failure and stop; do not start a daemon or switch to a CLI/shell fallback.
- Do not substitute shell reads, file search, or Git plumbing.
- Start task-shaped work with `explore`. For one already-known symbol, start with `search`.
- Use `change` before a mutation and again after it. Write only through `edit` or `refactor`.
- Call `capabilities({domain: "<tool>", operation: "<operation>", detail: "schema"})` only when an operation's exact arguments are unclear.
- Report graph-backed paths and symbol IDs. Never invent a result when an operation returns no match.
