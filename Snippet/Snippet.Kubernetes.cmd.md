### Setup Alias

```shell
code ~/.zshrc 
alias k="kubectl"
```

---

### Version

```shell
kubectl version
```

---

### Apply

```shell
kubectl apply -f <file>.yml
```

---

### Show Pods

```shell
kubectl get pods
```

---

### Delete Pod

```shell
kubectl delete pod <pod-name>
```

---

### Get pod info

```shell
kubectl describe pod <pod-name>
```

--- 

### Create Deployment

```shell
kubectl create deployment <deployment-name> --image=<image-name>
```

---

### Show Deployment

```shell
kubectl get deployments
```

---

### Delete  Deployment

```shell
kubectl delete deployments <deployment-name>

kubectl delete -f=deployment.yaml

```

---

### Restart Deployment

```shell
kubectl rollout restart deployment <deployment-name>
```

---

### Get Deployment info

```shell
kubectl describe deployment <deployment-name>
```

---

### Show Services

```shell
kubectl get services
```

---

### Create Service

- NodePort, LoadBalancer, ClusterIP

```shell
kubectl expose deployment <deployment-name> --type=LoadBalancer --port=8080
```

---

### Get Service Info

```shell
kubectl describe services <service-name>
```

---

### Rollout History

```shell
kubectl rollout history deployment/<deployment-name>
```

---

### Revision

```shell
kubectl rollout history deployment/<deployment-name> --revision=<revision-id>
```

---

### Rollout State

```shell
kubectl rollout status deployment/<deployment-name>
```

---

### Roll back

```shell
kubectl rollout undo deployment/<deployment-name>
```

---

### Roll back to specific revision

```shell
kubectl rollout undo deployment/<deployment-name> --to-revision=<revision-id>
```

---

### Scale

- replicas: number of pods 

```shell
kubectl scale deployment/<deployment-name> --replicas=1
```

---

### Show Logs

```shell
kubectl logs <pod-name>
```

---

### Execute commands

```shell
kubectl exec -it <pod-name> bash
```

### Generate secret key

```shell
kubectl create secret generic jwt-secret --from-literal=JWT_KEY=<secret>
```

### Show secrets

```shell
kubectl get secrets
```

### Port Forward

```shell
kubectl port-forward <pod-name> 4222:4222
```