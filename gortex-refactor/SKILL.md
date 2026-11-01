---
name: gortex-refactor
description: "Rename, extract, split, or restructure code safely."
---
# Refactor with Gortex

1. Call `explore({operation: "task", task: "<refactor goal>"})` and resolve every target with `search`.
2. Run `change({operation: "impact", source: {symbols: ["<id>"]}})`. Before altering a signature, also run `change({operation: "verify", source: {changes: [{symbol_id: "<id>", new_signature: "<signature>"}]}})`.
3. Choose exactly one `refactor` operation: `rename`, `move`, `inline`, `delete`, or `apply_code_action`. For example: `refactor({operation: "rename", target: {symbol: "<id>"}, new_name: "<name>"})`.
4. Require `change` operations `detect`, `tests`, `guards`, and `contract` after the mutation. Resolve every violation before finishing.

## Required behavior

- Native Gortex MCP is mandatory for this MCP-configured workflow. If its callable tools are missing, report a Gortex MCP integration failure and stop; do not start a daemon or switch to a CLI/shell fallback.
- Do not substitute shell reads, file search, or Git plumbing.
- Start task-shaped work with `explore`. For one already-known symbol, start with `search`.
- Use `change` before a mutation and again after it. Write only through `edit` or `refactor`.
- Call `capabilities({domain: "<tool>", operation: "<operation>", detail: "schema"})` only when an operation's exact arguments are unclear.
- Report graph-backed paths and symbol IDs. Never invent a result when an operation returns no match.
