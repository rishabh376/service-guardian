# Architecture - service-guardian

> Helps SaaS platform teams control ownership handoffs in platform workflows with measurable guardrails.

**Pain:** Teams lose time and confidence because ownership handoffs still depends on scattered manual checks.  
**Success metric:** Reduce ownership handoffs review effort by 60% and catch regressions before production.

## Decision log

We chose K8s + go because the service needs to be deployed, observed, and rolled back under real production conditions. The architecture reflects the operational problem behind Helps SaaS platform teams control ownership handoffs in platform workflows with measurable guardrails.: we need something that ships quickly, is observable, and can be recovered without hand-waving.

We also prioritized Platform teams need safe defaults and guardrails. This scaffold protects developers from dangerous cluster changes. and Service catalogs and self-service APIs are backed by telemetry so teams can move fast and still stay safe. so the architecture is built around real operational signal, not just feature scope.

See `docs/architecture/ADR-001-runtime-choice.md`

## Components

- go service with health, readiness, and domain-specific endpoints for Helps SaaS platform teams control ownership handoffs in platform workflows with measurable guardrails.
- Prometheus metrics and structured logging for operators
- Docker image with non-root runtime and secure defaults
- K8s Deployment + HPA 2-10, 70% CPU
- GitOps (FluxCD) and rollback scripts
- The operational stack implied by the project: Backstage, Crossplane, ArgoCD, Kubernetes Operators, Vault

## Trade-offs

| Choice | Why | Cost |
|---|---|---|
| K8s over serverless | team expertise, portability, predictable ops | more YAML |
| Self-hosted observability | lower cost than SaaS alternatives | we run it |
| RollingUpdate first | simpler for v0.1, canary later | faster shipping |

## Data flow

```
Client -> Ingress -> Service -> Pod
Pod -> /metrics -> Prometheus -> Alertmanager -> Slack
Domain actions -> API -> logs/metrics -> operators
```

## Scaling

HPA 2-10 pods. Stateless. 50m/64Mi request.

## Why not...

- **Serverless?** Cold start would hurt the main user flow and violate the reliability target.
- **Managed SaaS only?** The project must remain cost-effective and under operational control.
