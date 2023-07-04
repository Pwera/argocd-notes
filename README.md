# argocd notes

Installing on Windows
``` bash
SET GIT_REPO=https://github.com/Pwera/argocd-notes
SET GIT_TOKEN=<token>
scoop install argocd-autopilot
scoop install argocd

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d
```

Create project
```bash
argocd-autopilot project create testing

argocd-autopilot app create hello-world --app github.com/argoproj-labs/argocd-autopilot/examples/demo-app/ -p testing --wait-timeout 2m

argocd-autopilot app create hello-world2 --app github.com/argoproj-labs/argocd-autopilot/examples/demo-app/ -p testing --wait-timeout 2m
```

List accounts 
```bash
argocd account list
NAME   ENABLED  CAPABILITIES
admin  true     login
```




argocd app create nginx --repo https://charts.bitnami.com/bitnami --helm-chart nginx --revision 13.2.10 --dest-server https://kubernetes.default.svc --dest-namespace nginx




ヾ(⌐■_■)ノ♪
kubectl port-forward svc/argocd-server -n argocd 8080:80