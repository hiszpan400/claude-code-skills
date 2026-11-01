---
name: gortex-explore
description: "Understand how code works or trace an execution flow."
---
# Explore a Codebase with Gortex

1. Call `explore({operation: "task", task: "<question>"})`.
2. Read only a returned anchor with `read({target: {symbol: "<id>"}})`.
3. Choose the needed relationship (`callers`, `usages`, or `dependencies`), for example `relations({operation: "callers", target: {symbol: "<id>"}})`; use `trace({operation: "call_chain", target: {symbol: "<id>"}})` for execution order.
4. Answer with the execution path, file locations, symbol IDs, and any graph uncertainty.

## Required behavior

- Native Gortex MCP is mandatory for this MCP-configured workflow. If its callable tools are missing, report a Gortex MCP integration failure and stop; do not start a daemon or switch to a CLI/shell fallback.
- Do not substitute shell reads, file search, or Git plumbing.
- Start task-shaped work with `explore`. For one already-known symbol, start with `search`.
- Use `change` before a mutation and again after it. Write only through `edit` or `refactor`.
- Call `capabilities({domain: "<tool>", operation: "<operation>", detail: "schema"})` only when an operation's exact arguments are unclear.
- Report graph-backed paths and symbol IDs. Never invent a result when an operation returns no match.
