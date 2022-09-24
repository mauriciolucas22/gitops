```
kind create cluster --name kong-k8s --config infra/kong/kind/config.yaml

```

# install kong

```
kubectl create -f https://bit.ly/k4k8s
```

# Install Argo CI

```
kubectl create namespace argocd

kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

# View resources od argocd namespace

```
kubectl get all -n argocd
```

# Get ArgoCI admin password

```
kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo
```

## Forwording port argo

```
kubectl port-forward svc/argocd-server -n argocd 8080:443
```

# Apply ingress

```
kubectl apply -f k8s/ingress.yaml
```

# Port forward to kong service

```
kubectl port-forward -n kong svc/kong-proxy 8000:80
```

# Try

http://localhost:8000/server
