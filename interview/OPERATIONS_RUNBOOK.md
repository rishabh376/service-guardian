# Operations Runbook - service-guardian

Helps SaaS platform teams control ownership handoffs in platform workflows with measurable guardrails.

**On-call? Read this first.**

## Deploy
```
kubectl apply -k k8s/ -n service-guardian
kubectl rollout status deploy/service-guardian -n service-guardian
```

## Rollback (when things go red)
```
./scripts/rollback.sh
# usually < 30sec
```

## Scale up NOW
```
kubectl scale deploy/service-guardian --replicas=10 -n service-guardian
```

## Logs
```
kubectl logs -l app=service-guardian -n service-guardian -f --tail=200
```

## Crashloop?
```
kubectl describe pod -l app=service-guardian -n service-guardian
kubectl logs <pod> --previous -n service-guardian
```
90% of the time: missing env var in ConfigMap.

## Metrics
`curl localhost:8080/metrics` or Grafana dashboard in `monitoring/`

## DR / Failover
See `docs/DISASTER_RECOVERY.md` - RTO 15m

We actually tested this. 11 min.
