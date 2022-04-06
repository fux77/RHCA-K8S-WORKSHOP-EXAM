1
## webapp.yaml


```

apiVersion: apps/v1
kind: Deployment
metadata:
  creationTimestamp: null
  labels:
    app: webapp
  name: webapp
spec:
  replicas: 5
  selector:
    matchLabels:
      app: webapp
  strategy: {}
  template:
    metadata:
      creationTimestamp: null
      labels:
        app: webapp
    spec:
      containers:
      - image: nginx
        name: nginx
        resources: {}
status: {}

```

``` kubectl apply -f webapp.yaml  ```

2  ```  kubectl rollout status deploy webapp  ```

3  ```  kubectl get rs -l app=webapp  ```

4  ``` kubectl get rs -l app=webapp -o yaml > rs-webapp.yaml  ```

```  kubectl get pods -l app=webapp -o yaml > pods-webapp.yaml  ```

5  ```  
