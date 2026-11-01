---
name: gortex-episode-replay
description: "Reconstruct what changed in a window (postmortem, release, PR)."
---
# Replay a Change Episode with Gortex

1. Run `analyze({kind: "replay", options: {from: "<start>", to: "<end>"}})` for the requested window.
2. Project the relevant diff with `change({operation: "detect", source: {scope: "<scope>"}})`.
3. Surface decisions with `recall({operation: "surface", arguments: {task: "<episode>"}})`.
4. Trace important before/after paths using `trace` and identify which change altered behavior.
5. Produce a timestamped narrative with evidence links, impact, missed signals, and remaining uncertainty.

## Required behavior

- Native Gortex MCP is mandatory for this MCP-configured workflow. If its callable tools are missing, report a Gortex MCP integration failure and stop; do not start a daemon or switch to a CLI/shell fallback.
- Do not substitute shell reads, file search, or Git plumbing.
- Start task-shaped work with `explore`. For one already-known symbol, start with `search`.
- Use `change` before a mutation and again after it. Write only through `edit` or `refactor`.
- Call `capabilities({domain: "<tool>", operation: "<operation>", detail: "schema"})` only when an operation's exact arguments are unclear.
- Report graph-backed paths and symbol IDs. Never invent a result when an operation returns no match.
