# Copilot Instructions — paisabarbad

> Auto-generated from RNA schema v1.0.0. Edit `.rna/rna-schema.json` and re-run the adapter to update.

## Project Context

| Field | Value |
|-------|-------|
| Project | paisabarbad |
| Description | PaisaBarbad — sarcasm-first review aggregator, built with RNA Method |
| Domain | web-app |
| Stack | TypeScript · Next.js · React 19 · Tailwind CSS 4 · Static Export · GitHub Pages |
| Deployment | github-pages |

All agents should use this project context when making decisions about code style, tooling, and architecture.

## Development Standards

Write simple, readable code. Use early returns. Minimal diffs — change only what the task requires. DRY principle. Prefix event handlers with 'handle'. Document public functions with JSDoc.

## Context Router

Before responding, check if the request matches an existing rule, skill, or agent. Suggest the match to the user. Never mention the router when no match is found.

## Agent Collective

| Agent | Role | Invoke |
|-------|------|--------|
| Abhishek | Director / Orchestrator | `/abhishek <task>` |
| Developer | Full-Stack Developer | `/dev <task>` |
| Reviewer | Code Reviewer / Security Analyst | `/reviewer <task>` |
| Architect | System Architect | `/architect <task>` |
| Researcher | Explorer / Researcher | `/researcher <task>` |
| Ops | Operator / Automation Specialist | `/ops <task>` |
| Designer | UI/UX & Design System | `/designer <task>` |

## Available Skills

| Skill | Owner Agent | Trigger Keywords |
|-------|-------------|------------------|
| Smart Dev Agent | developer | implement, build, fix, debug, optimize, refactor |
| Design Quality | developer | audit UI, normalize, polish, critique, distill, harden, design quality |

## Slash Commands

| Command | Agent | Description |
|---------|-------|-------------|
| `/abhishek` | abhishek | Invoke Director — orchestration and coordination |
| `/dev` | developer | Invoke Developer — full-stack development |
| `/reviewer` | reviewer | Invoke Reviewer — code review and security |
| `/architect` | architect | Invoke Architect — system design |
| `/researcher` | researcher | Invoke Researcher — exploration and research |
| `/ops` | ops | Invoke Ops — operations and automation |
| `/designer` | designer | Invoke Designer — UI/UX and design system |
| `/join` | abhishek | Initiate a multi-agent join |
| `/team` | abhishek | Show team status |
| `/signals` | abhishek | Show signal queue and stale checkpoints |

## Joining Pipelines

| Pipeline | Agents | Flow |
|----------|--------|------|
| Dev → Review |  | Developer implements, Reviewer validates before merge |
| Design → Build |  | Designer creates UI specs, Developer implements, Reviewer validates |
| Research → Architect → Build |  | Researcher investigates, Architect designs, Developer implements |

## Session Protocol

**At the start of every session, the active agent must:**
1. Read `_memory/rna-method/timeline.json` — note the current phase, last decisions, open questions.
2. Read `_memory/rna-method/receptors.json` — identify active signal routes for this agent.
3. Announce: "I am [Agent Name]. I see [N] active signals. [Summary or 'queue is clear.']"

**At the end of every session:**
1. Archive key decisions to `_memory/agents/<id>/YYYY-MM-DD_<task-slug>_session.md`.
2. Update `knownDecisions[]` and `openQuestions[]` in `timeline.json`.
3. Record the exact stopping point if work is incomplete.
