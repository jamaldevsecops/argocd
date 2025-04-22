### Install Argo CD:
```sh
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```
### Verify Instllaiton
```sh
kubectl get pods -n argocd
```

