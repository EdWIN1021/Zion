## How to use env variables

### Step1

- generate secret key

```shell
kubectl create secret generic jwt-secret --from-literal=JWT_KEY=secret
```

### Step2

- check the key

```shell
kubectl get secrets
```

### Step3

- add to yaml file

```yaml
containers:
  - name: <container-name>
    image: <image-name>
    env:
      - name: JWT_KEY
        valueFrom:
          secretKeyRef:
            name: jwt-secret
            key: JWT_KEY
```