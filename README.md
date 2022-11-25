# ArgoCD
Installation

On Kubernetes Control Node

```text-plain
kubectl get nodes
```

```text-plain
kubectl create namespace argocd
```

```text-plain
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

```text-plain
sudo curl --silent --location -o /usr/local/bin/argocd https://github.com/argoproj/argo-cd/releases/download/v2.5.2/argocd-linux-amd64
```

```text-plain
sudo chmod +x /usr/local/bin/argocd
```

```text-plain
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
```

save the password

```text-plain
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

Open another ssh window to Kubernetes Control Node

```text-plain
argocd login localhost:8080
```
