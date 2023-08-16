
```yml
kubectl -n argocd create secret generic autopilot-secret --from-literal git_username=<your_username> --from-literal git-token=<your_token>
kubectl apply -f argo-cd.yaml
```