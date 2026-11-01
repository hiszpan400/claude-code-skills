---
name: gstack
description: >
  Master skill registry and stack navigator. Use when the user asks "what skills do I have",
  "which skill should I use for X", "show me available skills", "find a skill for Y",
  "what's in my skill stack", or starts a new project/task and needs to know what tools
  are available. Reads the live skill catalog from Obsidian vault. Also triggers auto-sync
  of installed skills to Obsidian when asked to "sync skills" or "update skill stack".
---

# GStack — Skill Stack Navigator

## Source of Truth
The complete skill catalog lives in Obsidian:
`~/jarvis sphere/obsidian-vault-starter/07-system/skill-stack.md`

Read it before recommending skills. Do NOT rely on system_reminder skill list alone — 
the Obsidian catalog has richer context, groupings, and "when to use" guidance.

## How to Use

1. **Find a skill for a task**: Read skill-stack.md, find the category, recommend the exact skill name.
2. **Show skill stack**: Output the table from skill-stack.md grouped by category.
3. **Sync skills to Obsidian**: Run the sync script below to update the catalog.

## Sync Command (update Obsidian catalog)

When asked to sync or when new skills are installed:

```bash
~/.claude/scripts/sync-skills-to-obsidian.sh
```

## Token Economy

Loading skill-stack.md (~3KB) costs ~750 tokens ONCE vs system_reminder listing 121+ skills
with descriptions every turn. Projects referencing Obsidian skill-stack instead of loading
all local SKILL.md files saves ~2,000 tokens/turn.

## Project Integration

All projects should have in their `.claude/CLAUDE.md`:
```
## Skills
Load skill catalog on-demand from Obsidian:
~/jarvis sphere/obsidian-vault-starter/07-system/skill-stack.md
```

This replaces bloated per-project skills directories for most use cases.
