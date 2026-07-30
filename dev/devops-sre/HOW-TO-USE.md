# DevOps / SRE Expert — How To Use

**Skill:** `devops-sre`
**Category:** Dev
**Author:** YourVisionYourCreation LLC
**License:** CC BY 4.0

---

## What This Skill Does

DevOps / SRE Expert makes Claude operate infrastructure like a site
reliability engineer, not a tutorial author. It covers the full stack of
production operations — Kubernetes, Terraform, CI/CD pipeline design, the
observability triad (metrics, logs, traces), SLO/error-budget design,
deployment strategies, incident response, and postmortems — with hard
verification gates before any infrastructure change ships.

---

## The Problem It Solves

Infrastructure advice without operational discipline produces the outages
it was supposed to prevent: `:latest` tags in production, secrets in the
repo, deploys with no rollback plan, services with no probes, and
`kubectl apply` from somebody's laptop. This skill hard-codes the rules
that keep production boring:

- Every deploy reversible within 5 minutes
- Rollback plan written **before** the change, not during the incident
- Blast radius stated on every infrastructure PR
- GitOps only — no manual applies to production
- Every failure path emits a log with context

---

## Quick Start

```
Write a production-grade Kubernetes deployment for this API — probes,
resource limits, security context, the works.
```
```
Design the CI/CD pipeline for this repo: lint through signed images to
gated prod deploy.
```
```
Define SLOs for this service and the burn-rate alerts that go with them.
```
```
Pods keep going CrashLoopBackOff after deploy — diagnose.
```

---

## Key Disciplines

| Area | The Standard |
|---|---|
| Pipelines | Six stages in order: lint → build → test → scan → sign → deploy |
| Images | Pinned to digest or semver — `:latest` never ships |
| Secrets | SOPS, sealed-secrets, or a vault — never the repo |
| Probes | Liveness + readiness on every service, startup probe for slow starters |
| SLOs | User-perspective SLIs, error budgets, burn-rate alerts at 2/5/10% |
| Rollouts | Rolling by default; canary with automated rollback on budget breach |
| Changes | Plan output reviewed, staging dry-run, rollback documented, on-call acked |

---

## What This Skill Will Not Do

- Ship a service without probes, limits, or a graceful-shutdown path
- Approve an infrastructure change without a written rollback plan
- Put a secret anywhere near version control
- Treat a restarted pod as a resolved incident

---

## Installation

1. Copy the `SKILL.md` file from this folder
2. Place it in your Claude skills directory
3. Install `shared-kernel` (from `agentic/`) alongside it — this skill
   loads it first
4. It activates automatically on any deploy, CI/CD, Kubernetes,
   Terraform, observability, or reliability task

---

*Part of the YVYC Claude Skills Library — Dev Category*
*YourVisionYourCreation LLC — [yourvisionyourcreation.com](https://www.yourvisionyourcreation.com)*
*Licensed under CC BY 4.0 — Free to use with attribution to YourVisionYourCreation LLC*
