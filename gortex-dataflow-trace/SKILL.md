---
name: gortex-dataflow-trace
description: "Trace where a value flows through the code."
---
# Trace Data Flow with Gortex

1. Call `explore({operation: "task", task: "trace <value> from <source> to <sink>"})`.
2. Resolve endpoints with `search({operation: "symbols", query: "<source or sink>"})`.
3. Use `trace({operation: "flow", target: {symbol: "<source-id>"}, to: {symbol: "<sink-id>"}})`. Use operation `taint` when source/sink security semantics matter.
4. Cross-check control flow with operation `call_chain` when the data-flow graph has a gap.
5. Report each hop with its symbol ID and confidence; distinguish no path from incomplete indexing.

## Required behavior

- Native Gortex MCP is mandatory for this MCP-configured workflow. If its callable tools are missing, report a Gortex MCP integration failure and stop; do not start a daemon or switch to a CLI/shell fallback.
- Do not substitute shell reads, file search, or Git plumbing.
- Start task-shaped work with `explore`. For one already-known symbol, start with `search`.
- Use `change` before a mutation and again after it. Write only through `edit` or `refactor`.
- Call `capabilities({domain: "<tool>", operation: "<operation>", detail: "schema"})` only when an operation's exact arguments are unclear.
- Report graph-backed paths and symbol IDs. Never invent a result when an operation returns no match.
