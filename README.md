# Swift Performance Engineering

An agent skill for generating, modifying, and reviewing Swift and iOS code with performance as a first-class concern.

This skill is built for Swift, SwiftUI, UIKit, and general iOS app engineering. It helps agents make better implementation choices before bottlenecks land in the codebase, and it also supports focused review and profiling follow-up when performance issues already exist.

## What This Skill Covers

- Object creation discipline
- Resource lifecycle safety
- Loop and hot-path efficiency
- Data-structure fit
- Algorithmic efficiency
- Memory management
- Concurrency and threading
- UI rendering and responsiveness
- Startup and first-frame time
- Quality-gate alignment

## When To Use This Skill

Use this skill whenever an agent is:

- generating new Swift or iOS code
- modifying or refactoring Swift, SwiftUI, or UIKit code
- implementing latency-sensitive or launch-sensitive features
- investigating UI hitches, startup issues, memory churn, or contention
- performing a performance-focused code review

## Quick Start

Invoke the skill explicitly in your agent:

```text
$swift-performance-engineering
```

Or use natural language:

```text
Use the swift performance engineering skill while implementing this SwiftUI feature.
Use the swift performance engineering skill while refactoring this UIKit screen for lower launch cost.
Use the swift performance engineering skill to review this code for memory, threading, and UI performance issues.
```

## What The Skill Contains

- [SKILL.md](/Users/aayushipandit/Desktop/Space/AgenticSkills/swift-performance-engineering/SKILL.md): trigger rules, workflow, build rules, and output expectations
- [review-checklist.md](/Users/aayushipandit/Desktop/Space/AgenticSkills/swift-performance-engineering/references/review-checklist.md): build-time and review-time checklist
- [official-performance-sources.md](/Users/aayushipandit/Desktop/Space/AgenticSkills/swift-performance-engineering/references/official-performance-sources.md): official Apple and Swift documentation index with direct links and search anchors
- [openai.yaml](/Users/aayushipandit/Desktop/Space/AgenticSkills/swift-performance-engineering/agents/openai.yaml): UI metadata for compatible tools

## How It Works

The skill is meant to stay active while code is being written, changed, or reviewed.

It pushes agents to:

- avoid predictable performance regressions in the first implementation
- choose better ownership, concurrency, and data-structure patterns
- keep expensive work off the main thread when safe
- justify recommendations with official Apple and Swift sources when needed
- leave a clear verification path using profiling, benchmarks, or metrics

## Official Grounding

This skill is not itself an official Apple document, but it is grounded in official sources. The reference index includes direct Apple Developer and Swift.org pages for launch time, SwiftUI performance, main-thread analysis, memory diagnostics, MetricKit, concurrency guidance, and language documentation.

See [official-performance-sources.md](/Users/aayushipandit/Desktop/Space/AgenticSkills/swift-performance-engineering/references/official-performance-sources.md).

## Best Fit

This skill is especially useful for:

- feed screens, timelines, lists, and grids
- app launch and first-frame optimization
- async image loading and caching
- state-heavy SwiftUI views
- UIKit screens with layout or scrolling pressure
- async/await adoption and contention analysis

## Compatibility

The skill is written to be portable across agent tools, including:

- Codex
- Claude Code
- Cursor
- Gemini
- other tools that support the Agent Skills format

## License

The Swift-performance-engineering Agent skill was originally created by Anurag Pandit. It is available under the MIT License, which permits commercial use, modification, distribution, and private use.

See [LICENSE](/Users/aayushipandit/Desktop/Space/AgenticSkills/swift-performance-engineering/LICENSE).

## Related Repository

This skill lives inside the broader [AgenticSkills](/Users/aayushipandit/Desktop/Space/AgenticSkills/README.md) repository, which is intended to become a central iOS-focused skill library.
