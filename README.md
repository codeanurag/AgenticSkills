# AgenticSkills

Portable, reusable agent skills for iOS development.

This repository is a centralized library of agent skills that can be used across Codex, Claude Code, Cursor, Gemini, and other tools that support the Agent Skills format. The primary focus is iOS engineering: Swift, SwiftUI, UIKit, concurrency, performance, architecture, migration work, and related workflows.

## What Is A Skill?

A skill is a structured bundle of instructions and supporting references that helps an AI coding agent behave like a more specialized iOS engineer.

In practice, a skill usually contains:

- `SKILL.md`: the core instructions and trigger metadata
- `agents/openai.yaml`: UI metadata for tools that surface skills directly
- `references/`: optional deeper guidance the agent can load only when needed
- `scripts/` or `assets/`: optional reusable tooling or files

Skills are designed to be:

- Portable: usable across multiple agent tools
- Reusable: invoked repeatedly across projects and teams
- Focused: small enough to stay useful without wasting context

## Quick Start

Clone the repo:

```bash
git clone https://github.com/<your-org-or-user>/AgenticSkills.git
cd AgenticSkills
```

Then use a skill in your preferred agent tool.

Examples:

- Codex: `$swift-performance-engineering`
- Claude Code: use the skill by name if installed in your skills environment
- Natural language: `Use the swift performance engineering skill while implementing this SwiftUI feature`

If your tool supports direct skill installation from a Git repository, point it at this repository and install the specific skill folder you want.

## Repository Structure

```text
AgenticSkills/
├── README.md
├── swift-performance-engineering/
│   ├── README.md
│   ├── SKILL.md
│   ├── agents/
│   │   └── openai.yaml
│   └── references/
│       ├── official-performance-sources.md
│       └── review-checklist.md
```

## How To Use A Skill

1. Pick the skill that matches the task.
2. Invoke it explicitly by name, or use natural language that clearly calls for that specialization.
3. Keep the skill active while generating, modifying, or reviewing code.
4. Ask for focused output when needed, such as performance, architecture, accessibility, or migration risk.

Examples:

- `Use $swift-performance-engineering while implementing this feed screen.`
- `Use $swift-performance-engineering to refactor this UIKit screen for lower startup cost and less main-thread work.`
- `Use $swift-performance-engineering to review this PR for UI latency, memory churn, and contention issues.`

## Currently Available Skills

| Skill | Focus | Best Used For |
| --- | --- | --- |
| `swift-performance-engineering` | Swift and iOS performance discipline during code generation, modification, and review | Startup time, UI responsiveness, memory, concurrency, hot paths, lifecycle safety |

See [swift-performance-engineering/README.md] for the current skill.

## Design Principles

This repository favors skills that are:

- Practical: optimize real implementation choices, not generic theory
- Cross-agent: usable in Codex, Claude Code, Cursor, and similar tools
- iOS-first: centered on Swift, SwiftUI, UIKit, Apple platform APIs, and Apple engineering constraints
- Grounded: backed by official Apple and Swift documentation where appropriate

## Adding More Skills

This repo is intended to grow into a broader iOS-focused skill library.

## Inspiration

This repository direction was informed by strong open skill examples from the community:

- [twostraws/SwiftUI-Agent-Skill](https://github.com/twostraws/SwiftUI-Agent-Skill)
- [AvdLee/Swift-Concurrency-Agent-Skill](https://github.com/AvdLee/Swift-Concurrency-Agent-Skill)
- [AvdLee/SwiftUI-Agent-Skill](https://github.com/AvdLee/SwiftUI-Agent-Skill)
