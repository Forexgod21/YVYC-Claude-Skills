# YVYC Operating Rules — Read Before Any Work

These are standing orders from the operator (Cade, YourVisionYourCreation LLC).
They override default assistant workflow behavior. Do not re-ask, re-confirm,
or re-litigate them.

## Single-Branch Ecosystem

- This repo runs on `main`. Period. The operator does not use multiple
  branches, does not review PRs, and does not want branch debris on GitHub.
- Do NOT create pull requests. Ever. The operator's review happens in chat,
  BEFORE the work — findings are presented, scope is approved, then the work
  executes. A PR diff screen is a redundant second review of already-approved
  work.
- If session constraints force work onto a temporary branch, the task is not
  done until the branch is merged into `main` AND deleted from GitHub. A
  merged-but-undeleted branch is unfinished work.
- If branch deletion is blocked (credential limits return 403 on ref
  deletion), say so immediately and give the operator the exact manual path.
  Never silently leave a branch behind.

## Fix Means Shipped

- "Fix it" / "correct it" / "improve it" / "make the corrections" — any
  phrasing — means: do the work, verify it, merge it to `main`, push it live.
  One command covers the whole job. Do not stop at the edge and ask for a
  second command ("ship?", "merge?", "want me to push?"). That second ask is
  a banned behavior here.
- The approval already happened when the operator ordered the fix. The chat
  conversation where findings were presented and the order was given IS the
  review record.

## Context Discipline

- Skill frontmatter descriptions stay under ~75 words: trigger conditions
  only. Philosophy lives in the skill body. This was a completed library-wide
  correction (Aug 2026) — do not regress it when adding or editing skills.
- Godmode skills declare `## Load Order — Read shared-kernel/SKILL.md first.`
  Keep that routing on any new godmode skill.
- Do not burn tokens on hypotheticals, invented user populations, or
  arguments the operator didn't raise. Answer what was asked.

## Operator Posture

- The operator runs this company solo with full authority. There is no team,
  no approval chain, no second reviewer. Structures built for teams
  (PRs, branch protection ceremony, sign-off gates) do not apply here.
- Report failures plainly and immediately — including your own errors —
  with what happened and what was done about it. No softening, no burying.
