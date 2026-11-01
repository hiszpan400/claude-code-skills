# Claude Code Skills Library

A community collection of **124 skills** for [Claude Code](https://claude.ai/code) — the AI-powered CLI by Anthropic.

Skills extend Claude Code with reusable, composable behaviors invoked via `/skill-name` in any project.

---

## What are Claude Code Skills?

Skills are structured prompt files placed in `~/.claude/skills/<skill-name>/SKILL.md`. Claude Code loads them on demand, enabling:

- Consistent workflows across projects
- Domain-specific AI behaviors (security, architecture, testing, etc.)
- Multi-agent orchestration patterns
- Reusable checklists and review frameworks

---

## Install

```bash
# Clone the library
git clone https://github.com/hiszpan400/claude-code-skills.git

# Copy all skills to your Claude Code skills directory
cp -r claude-code-skills/* ~/.claude/skills/

# Or install a single skill
cp -r claude-code-skills/threat-modeling ~/.claude/skills/
```

Then invoke in Claude Code:
```
/threat-modeling
/security-hardening
/test-driven-development
```

---

## Skill Categories

### Security & Threat Analysis
| Skill | Description |
|---|---|
| `threat-modeling` | Automated STRIDE/DREAD threat modeling from code analysis |
| `security-hardening` | Harden services: Docker, APIs, auth, secrets |
| `security-reviewer` | Deep code security review with language-specific playbooks |
| `security-assessment` | Full security posture assessment |
| `0day-scanner` | Scan for zero-day class vulnerabilities |
| `attack-tree-construction` | Build attack trees for a given system |
| `stride-analysis-patterns` | STRIDE methodology patterns and templates |
| `tm-security-review` | Full security review pipeline |
| `tm-quick-security-assessment` | Fast security triage |
| `sast-configuration` | Configure SAST tooling for a project |
| `opengrep-rule-generator` | Generate OpenGrep SAST rules |

### Architecture & Design
| Skill | Description |
|---|---|
| `architecture-patterns` | Reference architecture patterns with trade-off analysis |
| `api-design-principles` | REST/GraphQL API design best practices |
| `microservices-patterns` | Microservices decomposition and communication patterns |
| `cqrs-implementation` | CQRS pattern implementation guide |
| `event-store-design` | Event sourcing and event store design |
| `saga-orchestration` | Distributed saga pattern orchestration |
| `projection-patterns` | Read model projection patterns |
| `mcp-builder` | Build new MCP servers for Claude |
| `mcp-integration` | Integrate existing MCP tools |

### Development Workflow
| Skill | Description |
|---|---|
| `test-driven-development` | TDD workflow — write tests before code |
| `feature-development` | Structured feature development from spec to PR |
| `finishing-a-development-branch` | Pre-merge checklist and cleanup |
| `code-review` | Review diffs for bugs and improvement opportunities |
| `requesting-code-review` | Prepare code for review |
| `receiving-code-review` | Process and apply review feedback |
| `systematic-debugging` | Structured debugging methodology |
| `parallel-debugging` | Debug complex issues with parallel agents |
| `parallel-feature-development` | Multi-agent feature development |
| `verification-before-completion` | Verify changes work before marking done |

### Multi-Agent & Orchestration
| Skill | Description |
|---|---|
| `using-superpowers` | Multi-step complex task orchestration |
| `dispatching-parallel-agents` | Launch and coordinate parallel subagents |
| `subagent-driven-development` | Delegate implementation to specialized subagents |
| `workflow-orchestration-patterns` | Patterns for multi-agent workflows |
| `task-coordination-strategies` | Task decomposition and coordination |
| `team-composition-patterns` | Compose agent teams for complex tasks |
| `team-communication-protocols` | Inter-agent communication patterns |
| `claudex-loop` | Cross-review loop: Claude builds, Codex reviews |
| `agent-development` | Build custom Claude agents |

### Planning & Requirements
| Skill | Description |
|---|---|
| `writing-plans` | Structure implementation plans |
| `executing-plans` | Execute structured plans step by step |
| `plan-readiness-review` | Review a plan before execution |
| `prd-generator` | Generate Product Requirements Documents |
| `before-you-build` | Pre-build checklist and scoping |
| `brainstorming` | Structured brainstorming sessions |
| `phoenix-orchestrator` | Full Phoenix pipeline orchestrator |
| `phoenix-requirements-engineer` | Clarify and formalize requirements |
| `phoenix-scope-cutter` | Cut scope to what's essential |
| `phoenix-batch-planner` | Batch task planning |
| `phoenix-context-curator` | Curate context for complex tasks |
| `phoenix-constraint-distiller` | Extract hard constraints from requirements |
| `phoenix-contract-architect` | Design contracts between components |
| `phoenix-ambiguity-hunter` | Find and resolve ambiguities |
| `phoenix-security-engineer` | Security engineering in planning phase |
| `phoenix-pipeline-navigator` | Navigate multi-phase pipelines |
| `phoenix-verification-matrix` | Build verification checklists |
| `phoenix-research-pipeline` | Research pipeline for unknown domains |
| `phoenix-final-gate` | Final gate review before delivery |

### Production & Quality
| Skill | Description |
|---|---|
| `production-readiness-review` | Full production readiness checklist |
| `project-documenter` | Generate project documentation |
| `github-actions-templates` | CI/CD workflow templates |
| `hook-development` | Write Claude Code hooks |
| `writing-hookify-rules` | Automate behaviors with hooks |
| `skill-creator` | Create new skills for this library |
| `skill-development` | Develop and iterate on skills |
| `save-learning` | Persist learnings to memory |

### Frontend & UI
| Skill | Description |
|---|---|
| `frontend-design` | Frontend architecture and component design |
| `canvas-design` | Canvas-based UI design |
| `algorithmic-art` | Generative art with code |
| `web-artifacts-builder` | Build web artifacts and demos |
| `webapp-testing` | Test web applications end-to-end |
| `brand-guidelines` | Apply brand guidelines to UI |
| `theme-factory` | Generate UI themes |

### Content & Writing
| Skill | Description |
|---|---|
| `avoid-ai-writing` | Write in a natural human voice |
| `doc-coauthoring` | Collaborative documentation writing |
| `writing-skills` | Improve written communication |

### Reverse Engineering & Security Research
| Skill | Description |
|---|---|
| `reverse-engineer-anything` | Reverse engineer binaries, apps, protocols |
| `cti-domain-research` | Cyber threat intelligence domain research |

---

## Skill Structure

Each skill is a directory with a `SKILL.md` file:

```
~/.claude/skills/
└── my-skill/
    ├── SKILL.md          # Main skill definition (required)
    ├── references/       # Supporting reference material
    └── agents/           # Sub-agent prompts (for multi-agent skills)
```

`SKILL.md` frontmatter:
```yaml
---
name: my-skill
description: >
  One-paragraph description of what this skill does and when Claude should use it.
---
```

---

## Contributing

1. Fork this repo
2. Create your skill directory under a descriptive name
3. Add `SKILL.md` with frontmatter `name` and `description`
4. Submit a PR

Skills that get merged are tested against real Claude Code sessions.

---

## Related

- [Claude Code Documentation](https://docs.anthropic.com/claude-code)
- [Claude Code MCP Integration](https://docs.anthropic.com/claude-code/mcp)

---

**Maintained by [@hiszpan400](https://github.com/hiszpan400)**
