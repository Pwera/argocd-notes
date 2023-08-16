Manage argocd by itself, install ha mode - after that modify manifests.

```yml
kustomize build . | kubectl apply -f -
kubectl apply -f argocd-app.yaml -n argocd
```
