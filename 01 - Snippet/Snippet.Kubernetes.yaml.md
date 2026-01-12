## Deployment


```yaml
# https://kubernetes.io/docs/concepts/workloads/controllers/deployment/
apiVersion: apps/v1

kind: Deployment

metadata:
  name: <deployment-name>
  
spec:
  replicas: 1 # number of pods
  selector:
    matchLabels:
      app: <app-name>

  template:
    metadata:
      labels:
        app: <app-name>

    spec:
      containers: 
        - name: <container-name>
          image: <image-name>:<tag> # image on docker hub
          livenessProbe: # automatically restart containers
            httpGet:
			  path: /
			  port: 8080
          periodSeconds: 10
          initialDelaySeconds: 5

```

---

## Service

```yaml
apiVersion: v1
kind: Service
metadata:
  name: <service-name>

spec:
  selector:
    app: <deployment-name>

  ports:
    - protocol: TCP
      port: 80
      targetPort: <container-port>
  type: LoadBalancer
```