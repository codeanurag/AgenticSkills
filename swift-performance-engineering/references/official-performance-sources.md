# Official Performance Sources

Use these official Apple and Swift sources while designing, generating, modifying, and reviewing Swift/iOS code. Prefer direct canonical pages first; use the search anchors when Apple moves a page title or URL.

Last reviewed for this skill: 2026-03-08.

## Direct Apple Developer Pages

These are official Apple sources and were reachable when this skill was updated:

- `https://developer.apple.com/documentation/swiftui/performance-analysis`
  SwiftUI responsiveness, hangs, hitches, and links to deeper SwiftUI performance material.
- `https://developer.apple.com/documentation/xcode/understanding-and-improving-swiftui-performance`
  SwiftUI-specific guidance for long view updates and overly frequent updates.
- `https://developer.apple.com/tutorials/instruments/analyzing-main-thread-activity`
  Main-thread diagnosis workflow in Instruments.
- `https://developer.apple.com/documentation/xcode/reducing-your-app-s-launch-time`
  Current Apple guidance for launch-time reduction.
- `https://developer.apple.com/documentation/xcode/gathering-information-about-memory-use`
  Memory profiling entry point.
- `https://developer.apple.com/documentation/xcode/reducing-your-app-s-memory-use`
  Memory reduction guidance and follow-on topics.
- `https://developer.apple.com/documentation/xcode/diagnosing-memory-thread-and-crash-issues-early`
  Sanitizers and runtime diagnostics.
- `https://developer.apple.com/documentation/xcode/analyzing-the-performance-of-your-shipping-app`
  Organizer metrics for launch, memory, responsiveness, and battery.
- `https://developer.apple.com/documentation/metrickit/mxapplaunchmetric`
  Official launch metric API for post-release measurement.

## Direct Swift.org Pages

These are official Swift project sources:

- `https://www.swift.org/documentation/`
  Documentation index for language, standard library, and concurrency material.
- `https://www.swift.org/documentation/tspl/`
  The Swift Programming Language, the authoritative language reference.
- `https://www.swift.org/documentation/concurrency/`
  Complete concurrency checking and migration guidance.
- `https://www.swift.org/documentation/api-design-guidelines/`
  API design guidance relevant to maintainable performance-sensitive code.
- `https://www.swift.org/documentation/standard-library/`
  Standard library overview; collection behavior references route through official docs from here.
- `https://www.swift.org/blog/announcing-swift-6/`
  Swift 6 context for data-race safety and concurrency checks.

## Search Anchors

Use these searches to recover the current official page if a direct link changes:

### Apple

- `site:developer.apple.com "Improving app responsiveness"`
- `site:developer.apple.com "Reducing your app's launch time"`
- `site:developer.apple.com "Understanding and improving SwiftUI performance"`
- `site:developer.apple.com "Analyzing main thread activity"`
- `site:developer.apple.com "Gathering information about memory use"`
- `site:developer.apple.com "Reducing your app's memory use"`
- `site:developer.apple.com "Diagnosing memory, thread, and crash issues early"`
- `site:developer.apple.com "Analyzing the performance of your shipping app"`
- `site:developer.apple.com "MXAppLaunchMetric"`
- `site:developer.apple.com Instruments Time Profiler`
- `site:developer.apple.com Instruments Allocations`
- `site:developer.apple.com Instruments Leaks`

### Swift

- `site:swift.org "The Swift Programming Language"`
- `site:swift.org "Enabling Complete Concurrency Checking"`
- `site:swift.org "API Design Guidelines"`
- `site:swift.org "Standard Library"`
- `site:swift.org "Swift 6" concurrency data-race`

## How To Use These Sources

- In build mode, use the direct pages to justify architecture decisions before code lands: actor isolation, startup deferral, memory ownership, rendering updates, and measurement strategy.
- In review mode, use them to support findings and proposed fixes.
- Prefer Apple Developer docs for Instruments workflows, launch-time guidance, SwiftUI rendering behavior, main-thread rules, MetricKit, and memory profiling.
- Prefer Swift.org for concurrency, `Sendable`, language semantics, API design, and standard-library concepts.
- Prefer a short paraphrase plus a link over long quotations.
- If a source conflicts with current measured behavior, treat the recommendation as `possible` until profiled locally.

## Source Quality Notes

- Everything in the direct-link sections above is official Apple or official Swift project documentation.
- This file itself is not an official document; it is a curated index to official sources.
- Avoid relying on retired Apple archive pages except for historical background. If you mention one, label it as archived and non-current.

## Archived Apple References

Use only for historical context, not as primary evidence:

- `https://developer.apple.com/library/archive/documentation/Performance/Conceptual/LaunchTime/LaunchTime.html`
  Retired launch-time guidance. Useful for background only.

## Minimum Evidence By Topic

- Startup time: launch trace, signposts, Organizer or MetricKit launch metrics, plus Apple launch guidance.
- UI latency: frame pacing, main-thread analysis, SwiftUI or UIKit rendering evidence.
- Memory: allocations, memory graphs, leak evidence, or Organizer metrics plus ownership explanation.
- Contention: thread state, lock wait, actor hop, queue backlog, or hang diagnostics.
- Algorithms: complexity analysis tied to collection sizes, frequency, and user-visible paths.
