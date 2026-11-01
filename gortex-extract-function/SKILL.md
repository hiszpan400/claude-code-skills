---
name: gortex-extract-function
description: "Extract code into a function or method via LSP refactor."
---
# Extract a Function with Gortex

1. Inspect the file with `read({operation: "editing_context", target: {file: "<path>"}})`.
2. Resolve the selected range with `change({operation: "ranges", source: {file: "<path>", range: {...}}})`.
3. Request extraction actions with `change({operation: "code_actions", source: {file: "<path>", range: {...}}})`.
4. Apply the selected action through `refactor({operation: "apply_code_action", target: {file: "<path>"}, options: {...}})`.
5. Run `change` operations `detect`, `tests`, `guards`, and `contract`.

## Required behavior

- Native Gortex MCP is mandatory for this MCP-configured workflow. If its callable tools are missing, report a Gortex MCP integration failure and stop; do not start a daemon or switch to a CLI/shell fallback.
- Do not substitute shell reads, file search, or Git plumbing.
- Start task-shaped work with `explore`. For one already-known symbol, start with `search`.
- Use `change` before a mutation and again after it. Write only through `edit` or `refactor`.
- Call `capabilities({domain: "<tool>", operation: "<operation>", detail: "schema"})` only when an operation's exact arguments are unclear.
- Report graph-backed paths and symbol IDs. Never invent a result when an operation returns no match.
