---
name: gortex-rename
description: "Rename a symbol and update every reference atomically."
---
# Rename a Symbol with Gortex

1. Resolve exactly one symbol with `search({operation: "symbols", query: "<old name>"})`.
2. Enumerate references and implementations with `relations` operations `usages` and `implementations`.
3. Run `change({operation: "impact", source: {symbols: ["<id>"]}})`. For a public signature rename, also run `change({operation: "verify", source: {changes: [{symbol_id: "<id>", new_signature: "<signature with new name>"}]}})`.
4. Preview with `refactor({operation: "rename", target: {symbol: "<id>"}, new_name: "<new>", dry_run: true})`, then repeat it with `dry_run: false` to apply.
5. Require `change` operations `detect`, `guards`, and `tests`; confirm no old usages remain.

## Required behavior

- Native Gortex MCP is mandatory for this MCP-configured workflow. If its callable tools are missing, report a Gortex MCP integration failure and stop; do not start a daemon or switch to a CLI/shell fallback.
- Do not substitute shell reads, file search, or Git plumbing.
- Start task-shaped work with `explore`. For one already-known symbol, start with `search`.
- Use `change` before a mutation and again after it. Write only through `edit` or `refactor`.
- Call `capabilities({domain: "<tool>", operation: "<operation>", detail: "schema"})` only when an operation's exact arguments are unclear.
- Report graph-backed paths and symbol IDs. Never invent a result when an operation returns no match.
