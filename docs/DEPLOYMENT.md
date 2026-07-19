# Deployment - service-guardian

**Use case:** Helps SaaS platform teams control ownership handoffs in platform workflows with measurable guardrails.

## Infra requirements
→ `terraform/INFRA_REQUIREMENTS.md` - CPU/RAM/storage/network/cost breakdown

## GitOps
Flux watches `main` and reconciles changes automatically.

## Rollback
```
./scripts/rollback.sh
kubectl rollout undo deploy/service-guardian -n service-guardian
```
Usually < 30 sec.

## Cost
Supabase - $0/mo

Platform teams need safe defaults and guardrails. This scaffold protects developers from dangerous cluster changes.
