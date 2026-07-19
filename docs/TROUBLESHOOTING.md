# Troubleshooting - service-guardian

**CrashLoopBackOff**
`kubectl logs deploy/service-guardian -n service-guardian --previous`
Usually missing env var or bad config.

**ImagePullBackOff**
GHCR auth secret expired. `kubectl create secret docker-registry ...`

**500s spiking**
Check `/metrics`, then Prometheus alerts. Usually downstream timeout.

**Latency p95 high**
`kubectl get hpa -n service-guardian` - is it scaling? Check metrics-server.

**OOMKilled**
Bump memory limit in `helm/service-guardian/values.yaml`. Then find the leak.

**Flux won't sync**
`flux get kustomizations` - usually git repo URL rotated.
