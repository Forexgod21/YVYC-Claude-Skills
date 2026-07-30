# Swift / Apple Platforms Expert — How To Use

**Skill:** `swift-ios-expert`
**Category:** Dev
**Author:** YourVisionYourCreation LLC
**License:** CC BY 4.0

---

## What This Skill Does

Swift / Apple Platforms Expert makes Claude build for iOS, iPadOS, macOS,
watchOS, tvOS, and visionOS at current-generation standard: Swift 6
strict concurrency (actors, Sendable, isolation), the modern SwiftUI
state graph (`@Observable`, not `ObservableObject`), SwiftData with its
actor-boundary rules, UIKit interop where it's genuinely needed, and the
full ship path — testing, Instruments profiling, code signing, App Store
submission.

---

## The Problem It Solves

Apple's platform moves fast and AI output lags it by years: `@Published`
view models where `@Observable` belongs, force-unwraps in production,
`ModelContext` handed across actor boundaries (crash), `@MainActor` state
touched from background tasks (compile error in Swift 6, data race in
Swift 5). This skill writes for the platform as it is now:

- Version verification first — language mode 5 vs 6 and strict
  concurrency settings checked before any code
- A failure-mode table mapping the seven most common Swift/SwiftUI
  errors and crashes to their root causes
- Concurrency discipline that survives `SWIFT_STRICT_CONCURRENCY=complete`

---

## Quick Start

```
Build a settings screen: @Observable session model, SwiftData
persistence, working previews.
```
```
"Main actor-isolated property cannot be referenced" — fix this properly,
not with a hack.
```
```
Migrate this ObservableObject view model to @Observable.
```
```
This view has a retain cycle somewhere — find it.
```

---

## Key Disciplines

| Area | The Rule |
|---|---|
| Version check first | Language mode, deployment target, and strict concurrency confirmed before writing |
| Concurrency | Actor isolation respected; `@unchecked Sendable` only as documented last resort |
| SwiftUI state | `@Observable` era patterns; no mixing with `@StateObject` hierarchies |
| SwiftData | `ModelContext` never crosses actors — `PersistentIdentifier` does |
| Safety | No force-unwraps in production; `guard let` or it doesn't ship |
| Quality bar | Clean under warnings-as-errors, every view has a `#Preview`, `Logger` not `print()` |

---

## What This Skill Will Not Do

- Ship a force-unwrap to production
- Pass a `ModelContext` across an actor boundary
- Optimize before profiling with Instruments
- Write 2019-era Combine view models for an iOS 17+ target

---

## Installation

1. Copy the `SKILL.md` file from this folder
2. Place it in your Claude skills directory
3. Install `shared-kernel` (from `agentic/`) alongside it — this skill
   loads it first
4. It activates automatically on any Swift, SwiftUI, Xcode, or Apple
   platform task

---

*Part of the YVYC Claude Skills Library — Dev Category*
*YourVisionYourCreation LLC — [yourvisionyourcreation.com](https://www.yourvisionyourcreation.com)*
*Licensed under CC BY 4.0 — Free to use with attribution to YourVisionYourCreation LLC*
