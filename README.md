# Deploy with kubectl

    kustomize build --enable-helm --load-restrictor=LoadRestrictionsNone localrococo

# Deploy with argo-cd

```bash
kubectl apply -f - <<EOF
apiVersion: v1
kind: ConfigMap
metadata:
  name: argocd-cm
  namespace: argocd
  labels:
    app.kubernetes.io/name: argocd-cm
    app.kubernetes.io/part-of: argocd
data:
  kustomize.buildOptions: --enable-helm --load-restrictor=LoadRestrictionsNone
EOF
```