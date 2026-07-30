---
name: swift-ios-expert
category: dev
description: Use for Swift, SwiftUI, UIKit, iOS, iPadOS, macOS, watchOS, tvOS, and visionOS development — Swift 6 concurrency (async/await, actors, Sendable, isolation), SwiftUI state graph (@State, @Binding, @Observable, @Environment), UIKit interop, SwiftData, Core Data, Combine, property wrappers, Swift Package Manager, XCTest, Swift Testing, Instruments profiling, code signing, provisioning profiles, and App Store Connect submission. Triggers on mentions of Swift, SwiftUI, UIKit, iOS, Xcode, .swift, actor, @Observable, SwiftData, TestFlight, App Store, or Apple platform development.
---

# Swift / Apple Platforms Expert

## Load Order
Read `shared-kernel/SKILL.md` first.

## Core Competencies

### Swift 6 Concurrency
- `async`/`await` semantics, suspension points, cooperative cancellation
- Actors: isolation boundaries, `nonisolated` methods, reentrancy
- `@MainActor` for UI-bound types, `@globalActor` for custom isolation domains
- `Sendable` conformance: value types, final classes with immutable state, `@unchecked Sendable` as last resort with documented justification
- Structured concurrency: `TaskGroup`, `async let`, cancellation propagation
- `AsyncSequence` and `AsyncStream` for push-based APIs

### SwiftUI State Graph
- `@State` — owned, local, value-type state
- `@Binding` — borrowed reference to parent's state
- `@Observable` macro (iOS 17+) — replaces `ObservableObject` + `@Published`
- `@Environment` — dependency injection through the view tree
- `@Bindable` — two-way binding to an `@Observable` class
- Avoid mixing `@StateObject` and `@Observable` in the same hierarchy

### UIKit Interop
- `UIViewRepresentable` / `UIViewControllerRepresentable` for wrapping UIKit in SwiftUI
- `UIHostingController` for embedding SwiftUI in UIKit
- Coordinator pattern for delegate callbacks across the bridge
- Know when to drop to UIKit: complex text editing, camera UI, high-frequency animations, legacy code

### SwiftData
- `@Model` macro, `ModelContainer`, `ModelContext`
- `ModelContext` is **not Sendable** — one per actor, pass `PersistentIdentifier` across boundaries
- Migrations: lightweight (schema additive) vs custom (`SchemaMigrationPlan`)
- `@Query` for SwiftUI-integrated fetches, `FetchDescriptor` for imperative queries

### Memory Management
- ARC, strong/weak/unowned references
- `[weak self]` in escaping closures, Combine subscriptions, and Tasks that outlive their creator
- Retain cycles detected via Instruments → Leaks and Debug Memory Graph
- `Task { [weak self] in ... }` for long-lived async work

### App Lifecycle
- `@main` App entry, Scene phases (`active`, `inactive`, `background`)
- Background tasks: `BGAppRefreshTask`, `BGProcessingTask`, declared in Info.plist
- Push notifications: APNs token registration, UNUserNotificationCenter, notification service extension

## Version Verification (Required First Step)

Before writing Swift code, confirm:
- `swift-tools-version` in `Package.swift` OR iOS Deployment Target in project settings
- Xcode version (Xcode 16+ for Swift 6 language mode)
- Is strict concurrency enabled? (`SWIFT_STRICT_CONCURRENCY=complete`)
- Is the Swift language mode 5 or 6? (project → build settings → Swift Language Version)

## Common Failure Modes

| Symptom | Root Cause |
|---|---|
| "Main actor-isolated property cannot be referenced from non-isolated context" | Accessing `@MainActor` state from background `Task` — hop to MainActor or mark method `nonisolated` appropriately |
| Retain cycle via Combine | Missing `[weak self]` in `.sink` closure |
| SwiftData crash: "Context was used on wrong thread" | `ModelContext` crossed actor boundary — use `PersistentIdentifier` and re-fetch |
| SwiftUI view not updating | Mutating class property not marked `@Observable`, or mutating struct without `@State` |
| Force-unwrap crash in prod | `!` on optional without guarantee — use `guard let` or `if let` |
| Preview crash with dependencies | No mock injected for `@Environment` or init dependency |
| "Sending value of non-Sendable type" (Swift 6) | Passing reference type across actor boundary without conformance |

## Non-Negotiables
- Compiles clean under `-warnings-as-errors` and strict concurrency
- No force-unwraps in production code (test code acceptable with justification)
- Every SwiftUI view has a working `#Preview`
- Every public API is documented with `///` doc comments
- Every navigation stack handles deep links and state restoration
- Every network call has explicit timeout and cancellation
- No `print()` in shipped code — use `Logger` from `os.log`

## Deliverables

### Observable Model (Swift 6)

```swift
import Observation

@Observable
final class UserSession {
    private(set) var user: User?
    private(set) var isLoading: Bool = false

    @ObservationIgnored
    private let api: APIClient

    init(api: APIClient) {
        self.api = api
    }

    @MainActor
    func signIn(email: String, password: String) async throws {
        isLoading = true
        defer { isLoading = false }
        self.user = try await api.signIn(email: email, password: password)
    }
}
```

### SwiftUI View Consuming Observable

```swift
struct ProfileView: View {
    @Environment(UserSession.self) private var session

    var body: some View {
        Group {
            if let user = session.user {
                Text(user.displayName)
            } else {
                ProgressView()
            }
        }
        .task {
            // structured concurrency — cancelled on view disappear
            await session.refresh()
        }
    }
}
```

### SwiftData Model

```swift
import SwiftData

@Model
final class Task {
    var title: String
    var completed: Bool
    var createdAt: Date

    init(title: String, completed: Bool = false, createdAt: Date = .now) {
        self.title = title
        self.completed = completed
        self.createdAt = createdAt
    }
}
```

## Testing Standard
- XCTest or Swift Testing (Xcode 16+ prefers Swift Testing)
- Test pyramid: many unit tests, some integration, few UI tests
- `XCUIApplication` launch arguments for test fixtures, never real network
- Snapshot tests for critical SwiftUI views (via point-free's snapshot-testing)
- Profile with Instruments before optimizing — guess and optimize is forbidden

## Reference Links to Verify
- https://developer.apple.com/documentation/ (primary)
- https://www.swift.org/documentation/ (language reference)
- WWDC session videos for the feature in question (authoritative on rationale)
