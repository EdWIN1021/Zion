## How to create a pod


### Step1

- create a docker image

```shell
docker build -t <image-name> .
```

---

### Step2

- push the image to docker hub

```shell 
docker push <image-name>
```

---

### Step3

- create deployment

```shell 
kubectl create deployment <deployment-name> --image=<image-name>
```

---

### Step4

- create service

```shell
kubectl expose deployment <deployment-name> --type=LoadBalancer --port=8080
```

---

### Step5

- access [http://localhost:8080](http://localhost:8080)