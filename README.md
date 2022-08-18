# argocd-demo
ArgoDC Demo

## Deploy to ArgoCD to with Kustomize

If you want to deploy to ArgoCd with Kustomize your ArgoCD application should look something like this:

```
apiVersion: argoproj.io/v1alpha1
kind: Application

....

spec:
  destination:
    namespace: demo
    server: https://kubernetes.default.svc
  project: default
  source:
    path: overlays/prod
    repoURL: https://github.com/polinchw/argocd-demo-kustomize.git
    targetRevision: HEAD
  syncPolicy:
    automated:
      prune: true
      selfHeal: true
    syncOptions:
      - CreateNamespace=true


```