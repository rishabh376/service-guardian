# service-guardian

> Helps SaaS platform teams control ownership handoffs in platform workflows with measurable guardrails.

**Domain:** platform | **Complexity:** expert | **Stack:** Backstage, Crossplane, ArgoCD, Kubernetes Operators, Vault

| | |
|---|---|
| Use case | Helps SaaS platform teams control ownership handoffs in platform workflows with measurable guardrails. |
| Pain point | Teams lose time and confidence because ownership handoffs still depends on scattered manual checks. |
| Success metric | Reduce ownership handoffs review effort by 60% and catch regressions before production. |
| Cost | $0/mo on Supabase |

## Why this exists

Teams lose time and confidence because ownership handoffs still depends on scattered manual checks.. Helps SaaS platform teams control ownership handoffs in platform workflows with measurable guardrails.

> This project provides a golden path for internal teams, reducing onboarding friction and ticket volume. For this implementation, the service is designed to remove the operational friction behind Helps SaaS platform teams control ownership handoffs in platform workflows with measurable guardrails..

## What this product does

This project ships a production-oriented service that exposes health, readiness, observability, and domain-specific endpoints for Helps SaaS platform teams control ownership handoffs in platform workflows with measurable guardrails.. The implementation is intended to be deployed behind Kubernetes with secure defaults, CI validation, and rollback-ready manifests.

## Quick start

```bash
docker build -t service-guardian:local .
docker run -p 8080:8080 service-guardian:local
curl http://localhost:8080/healthz
```

## Architecture

```
GitHub CI -> Container Registry -> Kubernetes -> Backstage -> Operators / SRE
```

See `docs/ARCHITECTURE.md`

## Infrastructure

Full spec: `terraform/INFRA_REQUIREMENTS.md`

TL;DR: K8s cluster, 2-10 pods HPA, $0 on Supabase

## Docs

- `docs/ARCHITECTURE.md` - components, tradeoffs
- `docs/DESIGN_DISCUSSION.md` - how we decided to build this
- `docs/DEPLOYMENT.md` - GitOps, rollback
- `docs/SECURITY.md` - threat model
- `docs/TROUBLESHOOTING.md` - 3am runbook
- `terraform/INFRA_REQUIREMENTS.md` - **infra: CPU/RAM/storage/cost**

Interview prep: `interview/`
