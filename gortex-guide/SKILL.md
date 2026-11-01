---
name: gortex-guide
description: "Gortex reference: available tools, graph schema, and workflow."
---
# Gortex Guide

Use this sequence for codebase work:

1. `explore({operation: "task", task: "<goal or bug>"})` — localize the task and obtain the working set.
2. `search({operation: "symbols", query: "<name>"})` or `search({operation: "text", query: "<literal>"})` — resolve a precise anchor.
3. `read({operation: "source", target: {symbol: "<id>"}})` — read only the source needed.
4. `relations({operation: "usages", target: {symbol: "<id>"}})` or `trace({operation: "call_chain", target: {symbol: "<id>"}})` — follow verified graph edges.
5. `change({operation: "impact", source: {symbols: ["<id>"]}})` — assess a planned change.
6. Apply with `edit` or `refactor`, then run `change` operations `detect`, `guards`, and `tests`.

## Required behavior

- Native Gortex MCP is mandatory for this MCP-configured workflow. If its callable tools are missing, report a Gortex MCP integration failure and stop; do not start a daemon or switch to a CLI/shell fallback.
- Do not substitute shell reads, file search, or Git plumbing.
- Start task-shaped work with `explore`. For one already-known symbol, start with `search`.
- Use `change` before a mutation and again after it. Write only through `edit` or `refactor`.
- Call `capabilities({domain: "<tool>", operation: "<operation>", detail: "schema"})` only when an operation's exact arguments are unclear.
- Report graph-backed paths and symbol IDs. Never invent a result when an operation returns no match.
