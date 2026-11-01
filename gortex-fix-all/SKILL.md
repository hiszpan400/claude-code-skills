---
name: gortex-fix-all
description: "Clear LSP diagnostics — one error, a file, or source.fixAll."
---
# Fix Diagnostics with Gortex

1. Read diagnostics using `change({operation: "diagnostics", source: {file: "<path>"}})`.
2. Fetch applicable fixes with `change({operation: "code_actions", source: {file: "<path>"}})`.
3. Apply one reviewed action with `refactor({operation: "apply_code_action", target: {file: "<path>"}, options: {...}})`, or use operation `fix_all` only when the user asked for all safe fixes.
4. Re-run diagnostics, then run `change` operations `detect` and `tests`.

## Required behavior

- Native Gortex MCP is mandatory for this MCP-configured workflow. If its callable tools are missing, report a Gortex MCP integration failure and stop; do not start a daemon or switch to a CLI/shell fallback.
- Do not substitute shell reads, file search, or Git plumbing.
- Start task-shaped work with `explore`. For one already-known symbol, start with `search`.
- Use `change` before a mutation and again after it. Write only through `edit` or `refactor`.
- Call `capabilities({domain: "<tool>", operation: "<operation>", detail: "schema"})` only when an operation's exact arguments are unclear.
- Report graph-backed paths and symbol IDs. Never invent a result when an operation returns no match.
