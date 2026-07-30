# Angular Architect — How To Use

**Skill:** `angular-architect`
**Category:** Dev
**Author:** YourVisionYourCreation LLC
**License:** CC BY 4.0

---

## What This Skill Does

Angular Architect makes Claude write modern Angular the way the framework
is meant to be written today — standalone components, signals as the
primary reactive primitive, `inject()` over constructor injection, the new
control flow syntax, OnPush change detection everywhere — instead of the
2018-era NgModule patterns most AI output defaults to. It covers
architecture, implementation, SSR with hydration, typed reactive forms,
and Nx monorepo layout.

---

## The Problem It Solves

Untrained AI output for Angular has a signature failure: it writes for the
framework as it existed five versions ago. NgModules where standalone
belongs, constructor injection where `inject()` belongs, `*ngIf` where
`@if` belongs, subscriptions that leak because nobody added
`takeUntilDestroyed()`. This skill locks the modern baseline in and adds
the discipline most codebases are missing:

- A required version-verification step before any code gets written —
  the skill reads your `package.json` and `angular.json` posture first
- A signals-vs-RxJS decision table so the two reactive systems stop
  getting mixed at random
- A failure-mode table mapping eight common Angular symptoms straight to
  their root cause

---

## Quick Start

```
Build me a user profile feature: standalone component, signal-based
state, lazy-loaded route with an auth guard.
```
```
This component leaks memory over time — diagnose it.
```
```
Migrate this NgModule feature to standalone components and the new
control flow.
```
```
Set up SSR with hydration for this app and defer the below-the-fold
sections.
```

---

## Key Disciplines

| Discipline | The Rule |
|---|---|
| Version check first | Reads `package.json`, `angular.json`, and Nx presence before writing a line |
| Signals vs RxJS | Local/derived state → signals; streams, sockets, debounce → RxJS; bridge with `toSignal()` |
| Change detection | OnPush on every component, no exceptions |
| Subscriptions | `takeUntilDestroyed()` or the `async` pipe — nothing unmanaged |
| Templates | Every `@for` gets a `track`; no logic beyond simple checks |
| Forms | Typed reactive forms only — template-driven forms don't ship |

---

## What This Skill Will Not Do

- Write NgModule-first code for a standalone-capable project
- Leave a subscription unmanaged or an `@for` untracked
- Put HTTP calls in components instead of services
- Guess your Angular version instead of reading it from the repo

---

## Installation

1. Copy the `SKILL.md` file from this folder
2. Place it in your Claude skills directory
3. Install `shared-kernel` (from `agentic/`) alongside it — this skill
   loads it first
4. It activates automatically on any Angular, RxJS, NgRx, or Nx task

---

*Part of the YVYC Claude Skills Library — Dev Category*
*YourVisionYourCreation LLC — [yourvisionyourcreation.com](https://www.yourvisionyourcreation.com)*
*Licensed under CC BY 4.0 — Free to use with attribution to YourVisionYourCreation LLC*
