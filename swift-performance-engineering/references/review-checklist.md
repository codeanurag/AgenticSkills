# Swift Performance Engineering Checklist

Use this checklist both when generating or modifying Swift/iOS code and when reviewing existing code. In build mode, use it to prevent bottlenecks from landing. In review mode, use it to explain and prioritize issues already present.

## Build-First Expectations

- Design for the hot path before writing the first implementation.
- Make main-thread, allocation, and lifecycle costs explicit in architecture decisions.
- Prefer simple code when the path is not performance-sensitive; prefer disciplined code when the path is launch-, render-, scroll-, or interaction-critical.
- Add measurement hooks, performance tests, or profiling notes when a change could affect startup, rendering, memory, or concurrency behavior.

## Object Creation Discipline

- Hoist expensive objects out of loops, cell configuration, `body`, and frequently-called callbacks.
- Reuse `DateFormatter`, `ISO8601DateFormatter`, `NumberFormatter`, `JSONDecoder`, `JSONEncoder`, regex builders, and layout helpers when configuration is stable.
- Avoid creating detached tasks, view models, caches, or wrappers per render unless lifecycle truly requires it.
- Flag bridging that causes churn between Swift value types and Foundation reference types in hot paths.

## Resource Lifecycle Safety

- Check that observers, timers, display links, and tasks are cancelled or invalidated with owner lifetime.
- Look for caches with no limits, no eviction policy, or incorrect key granularity.
- Move heavyweight initialization out of app launch or first render unless it is essential for first interaction.
- Ensure expensive shared resources are created lazily and released when their owning feature disappears.
- When generating code, make ownership and teardown visible in the API shape instead of bolting cleanup on later.

## Loop And Hot-Path Efficiency

- Inline repeated derived work only once per pass; precompute when inputs are stable.
- Flag `filter` plus `first`, repeated sorting, repeated formatting, repeated parsing, and repeated `contains` scans on large arrays inside loops.
- Watch for accidental copy-on-write from mutation of shared arrays, dictionaries, strings, or data buffers.
- Avoid logging, allocation, decoding, and synchronization in animation, scroll, or layout paths.

## Data Structure Fit

- Prefer `Set` or dictionary lookup for membership and keyed access.
- Prefer contiguous arrays for small ordered collections and predictable iteration.
- Call out large structs copied across async boundaries, closures, or collection transforms.
- Check whether a cache, ring buffer, heap, or ordered dictionary better matches the access pattern than a plain array.

## Algorithmic Efficiency

- Estimate complexity at the call site, not just within a helper.
- Flag repeated whole-list transforms during incremental updates.
- Look for quadratic diffing, nested scans, redundant fetches, and repeated layout invalidation.
- Reduce duplicate work before proposing lower-level micro-optimizations.

## Memory Management

- Check capture lists, delegate ownership, task retention, and actor ownership for leaks.
- Watch image decode size, decompression timing, and unnecessary full-resolution retention.
- Flag temporary buffers or copied payloads that exceed the steady-state memory budget.
- Prefer streaming, chunking, or incremental parsing for large inputs.

## Concurrency And Threading

- Keep UI state changes on the main actor, but move parsing, mapping, persistence, and image work off it.
- Watch for actor ping-pong, serial-queue funnels, lock convoys, priority mismatches, and task explosions.
- Require explicit cancellation handling for search, scrolling, prefetching, and view-bound async work.
- Prefer structured concurrency to detached work unless ownership is clearly external.
- When generating code, choose actor boundaries, task ownership, and cancellation semantics before adding parallel work.

## UI Rendering And Responsiveness

- In SwiftUI, inspect identity stability, observable granularity, invalidation scope, and repeated work in `body`.
- In UIKit, inspect layout passes, cell reuse discipline, image decoding, text measurement, and synchronous main-thread I/O.
- Keep launch and first interaction paths free of nonessential work.
- Defer below-the-fold work, batch updates, and cache derived presentation state when safe.

## Quality Gate Alignment

- Reject changes that improve speed by weakening correctness, cancellation, testability, or lifecycle ownership.
- Prefer fixes that are measurable, local, and easy to verify in CI or Instruments.
- Call out missing metrics, missing regression tests, and missing observability when they block confidence.
- When generating code, document the intended verification path so later agents can confirm the design actually performs as expected.
