# k8s-gitops


## Structuur

```text
k8s-gitops/
├── apps/
│   └── nginx-gitops/           ← Helm chart die ArgoCD uitrolt
│       ├── Chart.yaml
│       ├── values.yaml         ← hier pas je de app aan (replicas, tekst, poort)
│       └── templates/
│           ├── configmap.yaml
│           ├── deployment.yaml
│           └── service.yaml
└── argocd/
    └── nginx-gitops-app.yaml   ← ArgoCD Application: koppelt apps/nginx-gitops aan namespace gitops
```

## Werkwijze

1. Wijzig `apps/nginx-gitops/values.yaml` en push naar `main`.
2. ArgoCD ziet de nieuwe commit en past het cluster automatisch aan.
3. Handmatige wijzigingen in het cluster worden door ArgoCD teruggezet (self-heal).

Git is daarmee de single source of truth.
