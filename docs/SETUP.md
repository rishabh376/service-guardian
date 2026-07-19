# Setup - service-guardian

Helps SaaS platform teams control ownership handoffs in platform workflows with measurable guardrails.

1. **Infra first**: `cd terraform && terraform init && terraform apply`
2. `kubectl apply -k k8s/ -n service-guardian`
3. `kubectl port-forward svc/service-guardian 8080:80 -n service-guardian`
4. `curl localhost:8080/healthz`

Env vars: `PORT=8080`, `LOG_LEVEL=info`

Service catalogs and self-service APIs are backed by telemetry so teams can move fast and still stay safe.
