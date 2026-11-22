# GitOps, ArgoCD et Observabilité

## Architecture
Dev -> Git (source de vérité) <- ArgoCD (pull) -> Kubernetes ; Prometheus scrape ArgoCD + podinfo ; Grafana + Alertmanager.
Pattern App-of-Apps : `bootstrap/root-app.yaml` déploie tout le contenu de `apps/`.

## Structure
- `bootstrap/` : root-app (seul `kubectl apply` manuel)
- `apps/` : Applications ArgoCD (podinfo-dev, monitoring-stack, monitoring-config)
- `base/` + `overlays/` : Kustomize (podinfo)
- `monitoring/` : ServiceMonitors, PrometheusRule, dashboard (ConfigMap)
- `dashboards-export/` : JSON du dashboard Grafana


