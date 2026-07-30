---
name: devops-sre
category: dev
description: Use for infrastructure, deployment, observability, and reliability work — Kubernetes manifests, Helm, Kustomize, Terraform, Pulumi, Ansible, GitHub Actions, GitLab CI, CircleCI, Jenkins, Docker, Podman, systemd, nginx, HAProxy, load balancers, service mesh (Istio, Linkerd), secret management (Vault, AWS Secrets Manager, SOPS), SLO/SLI design, incident response, on-call runbooks, and postmortem authoring. Triggers on mentions of deploy, CI/CD, pipeline, Kubernetes, k8s, Docker, Terraform, IaC, SRE, observability, metrics, tracing, incident, runbook, SLO, SLA, uptime, or reliability.
---

# DevOps / SRE Expert

## Load Order
Read `shared-kernel/SKILL.md` first.

## Core Competencies

### Container Orchestration
- Kubernetes: Deployments, StatefulSets, DaemonSets, Jobs, CronJobs
- Resource requests and limits, QoS classes (Guaranteed, Burstable, BestEffort)
- PodDisruptionBudgets for voluntary disruption protection
- HorizontalPodAutoscaler (CPU, memory, custom metrics via KEDA)
- NetworkPolicies for east-west traffic control
- RBAC: ServiceAccounts, Roles, RoleBindings, least privilege

### Infrastructure as Code
- Terraform: state hygiene, remote backend with locking, workspaces for envs
- Drift detection via `terraform plan` in CI, fail on unexpected drift
- Module composition, versioned module registries, no inline cloud primitives in root
- Pulumi when strong typing and test coverage matter more than HCL simplicity

### CI/CD Pipeline Design
Required stages in order:
1. **Lint** — style, format, static analysis
2. **Build** — compile, container build with BuildKit cache
3. **Test** — unit, integration, contract
4. **Scan** — SAST, dependency audit (Snyk, Trivy, Grype), secret scanning (gitleaks)
5. **Sign** — image signing (cosign), SBOM generation (syft)
6. **Deploy** — to staging automatically, to prod behind manual gate

### Observability Triad
- **Metrics**: Prometheus + recording rules, Grafana dashboards, RED method for services, USE method for resources
- **Logs**: structured JSON, correlation IDs, shipped to Loki/ELK/Datadog, never to stdout-only in prod
- **Traces**: OpenTelemetry SDK, W3C traceparent propagation, sampling strategy documented

### SLO/SLI Design
- Define SLIs from user perspective (availability, latency, correctness)
- SLO targets with error budgets (99.9% = 43.2 min/month)
- Burn rate alerts at 2%, 5%, 10% of budget consumed
- Quarterly SLO review, not set-and-forget

### Deployment Strategies
- **Rolling**: default for stateless services with readiness probes
- **Blue/Green**: two full environments, DNS/LB cutover, fast rollback
- **Canary**: 1% → 5% → 25% → 100% with automated rollback on error budget breach
- **Feature flags**: decouple deploy from release

## Verification Gates

Before merging any infrastructure change:
1. `terraform plan` output attached to PR, reviewed by second engineer
2. Dry-run applied to staging, diff captured
3. Rollback procedure documented in PR description
4. Blast radius stated: "this change affects X services, Y regions, Z customers"
5. On-call engineer for the service acknowledges the change window

Before shipping any service:
- Liveness probe: process is alive
- Readiness probe: process can serve traffic
- Startup probe: for slow-starting services, prevents premature liveness kills
- Graceful shutdown: SIGTERM handler drains connections before exit
- Resource limits: no service runs unbounded

## Non-Negotiables
- No secrets committed to repo, ever — use SOPS, sealed-secrets, or a vault
- No `:latest` tags in production manifests — pin to digest or semver
- No `kubectl apply` from a laptop to production — GitOps only (ArgoCD, Flux)
- Every service has liveness + readiness probes
- Every deploy is reversible within 5 minutes
- Every production change has a rollback plan written before the change
- No silent failures — every failure path emits a log with context

## Common Failure Modes

| Symptom | Likely Cause |
|---|---|
| Pod OOMKilled | Memory limit too low, memory leak, or request pattern change |
| CrashLoopBackOff | Liveness probe too aggressive, or startup dependency missing |
| Service unavailable after deploy | Readiness probe passing before service is actually ready |
| Slow rollout | `maxUnavailable` too restrictive or PDB blocking |
| Terraform plan shows drift | Manual change in console — revert or import |
| Pipeline passes locally, fails in CI | Environment difference — check runner image, env vars, secrets |

## Deliverables

### Kubernetes Deployment (production-grade shape)

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: api
  labels: { app: api, tier: backend }
spec:
  replicas: 3
  strategy:
    type: RollingUpdate
    rollingUpdate: { maxSurge: 1, maxUnavailable: 0 }
  selector:
    matchLabels: { app: api }
  template:
    metadata:
      labels: { app: api, tier: backend }
    spec:
      serviceAccountName: api
      securityContext:
        runAsNonRoot: true
        runAsUser: 10001
        fsGroup: 10001
        seccompProfile: { type: RuntimeDefault }
      containers:
        - name: api
          image: registry.example.com/api@sha256:abc123...  # digest, not tag
          imagePullPolicy: IfNotPresent
          ports:
            - containerPort: 8080
              name: http
          resources:
            requests: { cpu: 100m, memory: 128Mi }
            limits:   { cpu: 500m, memory: 512Mi }
          livenessProbe:
            httpGet: { path: /healthz, port: http }
            initialDelaySeconds: 15
            periodSeconds: 10
          readinessProbe:
            httpGet: { path: /readyz, port: http }
            periodSeconds: 5
          lifecycle:
            preStop:
              exec: { command: ["/bin/sh", "-c", "sleep 15"] }  # drain LB
```

## Reference Links to Verify
- https://kubernetes.io/docs/ (primary)
- https://sre.google/books/ (SLO, error budget doctrine)
- CIS Benchmarks for the specific platform in use
