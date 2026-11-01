---
name: gortex-safe-edit
description: "Preview an edit's blast radius on the shadow graph before writing."
---
# Make a Safe Edit with Gortex

1. Localize with `explore` and inspect `read({operation: "editing_context", target: {file: "<path>"}})`.
2. Run `change({operation: "impact", source: {symbols: ["<id>"]}})` before editing.
3. Choose `edit` operation `file`, `symbol`, or `batch`. Preview with `dry_run: true`; after review, repeat the same guarded request with `dry_run: false`. Use `change({operation: "simulate", source: {steps: "<WorkspaceEdit JSON array>"}})` for a multi-step semantic edit.
4. Run `change` operations `detect`, `tests`, `guards`, and `contract`. Signature verification belongs before mutation with the proposed signature.

## Required behavior

- Native Gortex MCP is mandatory for this MCP-configured workflow. If its callable tools are missing, report a Gortex MCP integration failure and stop; do not start a daemon or switch to a CLI/shell fallback.
- Do not substitute shell reads, file search, or Git plumbing.
- Start task-shaped work with `explore`. For one already-known symbol, start with `search`.
- Use `change` before a mutation and again after it. Write only through `edit` or `refactor`.
- Call `capabilities({domain: "<tool>", operation: "<operation>", detail: "schema"})` only when an operation's exact arguments are unclear.
- Report graph-backed paths and symbol IDs. Never invent a result when an operation returns no match.
