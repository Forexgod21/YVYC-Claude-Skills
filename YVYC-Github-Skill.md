---
name: yvyc-github-doctrine
version: 1.0
author: YourVisionYourCreation LLC
license: CC BY 4.0
category: godmode
description: >
  Governs how all git and GitHub work runs in the YVYC ecosystem:
  single-branch operation on main, fix-means-shipped in one command,
  review in chat before the work, and zero branch debris. Always-on
  for any task that touches a YVYC repository — committing, merging,
  pushing, or any suggestion involving branches or pull requests.
---

# YVYC GitHub Doctrine

## Load Order
Read `shared-kernel/SKILL.md` first.

---

## Universal So-What

Git's default ceremony — branches, pull requests, approval gates — was
built to separate the author from the approver on teams where those are
different people. In the YVYC ecosystem they are the same person: one
operator, full authority, no approval chain. Running team ceremony in a
solo operation doesn't add safety; it adds friction, second asks, and
branch debris the operator never wanted and has to clean up.

The review still happens. It happens in chat, before the work: findings
presented, scope approved, order given. The conversation is the review
record. Everything after that is execution.

---

## Core Doctrine

**1. Single branch. Main is the ecosystem.**
YVYC repos run on `main`. No feature branches, no long-lived side
branches, no PRs. If a session's own constraints force work onto a
temporary branch, that branch is scaffolding — it must be merged into
`main` and deleted before the task counts as done. A merged-but-living
branch is unfinished work.

**2. Fix means shipped.**
Any order to fix, correct, improve, upgrade, or make better — whatever
the word — means the full cycle: do the work, verify it, merge to
`main`, push live. One command covers the whole job. Stopping at the
edge to ask "ship it?" is a banned move. The approval already happened
when the order was given.

**3. The chat is the review surface.**
Findings are presented and scope is approved in conversation before the
work executes. Do not route already-approved work through a PR diff
screen for a second look. Do not create a pull request unless the
operator explicitly orders one.

**4. No silent debris, no silent failure.**
If a branch can't be deleted, a push is refused, or credentials block a
step, say so immediately with the exact manual path the operator can
take. Never end a task leaving remote state the operator doesn't know
about.

**5. Direct and traceable.**
Commit messages state what changed and why in plain language. History
lives in `git log` on main — that is the permanent record, with or
without ceremony around it.

---

## Banned Moves

| Move | Why it's banned |
|---|---|
| Creating a PR by default | Team ceremony in a solo ecosystem; review already happened in chat |
| Asking "want me to merge/ship/push?" after a fix order | Second ask on an already-given approval |
| Leaving a merged branch on the remote | Debris the operator must find and clean |
| Suggesting branch-based workflows "as best practice" | The world's default is not YVYC's default |
| Ending a task without reporting a blocked git step | Silent failure; operator discovers it later |

---

## Compliance Check (Run Before Closing Any Repo Task)

1. Is every change merged into `main` and pushed?
2. Are there zero branches on the remote other than `main`? If one
   remains and deletion is blocked, was the operator told, with the
   manual path?
3. Was the work shipped on the original order, without a second ask?
4. Does `git log` on main read as a clear record of what happened?

If any answer is no, the task is not done.

---

*YourVisionYourCreation LLC, yourvisionyourcreation.com*
*Licensed under CC BY 4.0*
