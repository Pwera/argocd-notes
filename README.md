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

Creating the backup
```bash
argocd admin export -n argocd > backup-$(date +"%Y-%m-%d_%H:%M").yml
```

Restoring the backup
```bash
argocd admin import - < backup-2021-09-15_18:16.yml
```

Port forward
```bash
kubectl port-forward pod/argocd-server-5df56f89ff-642c5 -n argocd 8080:8080
```


argocd app create nginx --repo https://charts.bitnami.com/bitnami --helm-chart nginx --revision 13.2.10 --dest-server https://kubernetes.default.svc --dest-namespace nginx




ヾ(⌐■_■)ノ♪
