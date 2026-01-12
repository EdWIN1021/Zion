## How to update pod

### Step1

- rebuild the image with new tag

```shell
docker build -t <image-name>:<new-tag> .
```

---

### Step2

- push the image to docker hub with new tag

```shell
docker push <image-name>:<new-tag>
```

---

### Step3

- find container name 

```shell
kubectl describe pod <pod-name>
```

---

### Step4

- update image with new tag

```shell
kubectl set image deployment/<deployment-name> <container-name>=<image-name>:<new-tag>
```

---

### Step5

- check the rollout state

```shell
kubectl rollout status deployment/<deployment-name>
```