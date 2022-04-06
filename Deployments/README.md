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

5  ```  kubectl delete deploy webapp  ```

```  kubectl get pods -l app=webapp -w  ```

6
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
  replicas: 1
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
      - image: nginx:1.17.1
        name: nginx
        ports:
        - containerPort: 80        
        resources: {}
status: {}

```

```  kubectl apply -f webapp.yaml  ```

```  kubectl describe deploy webapp | grep Image  ```

7  ```  kubectl set image deploy/webapp nginx=nginx:1.17.4  ```

```  kubectl describe deploy webapp | grep Image  ```

8  ```  kubectl rollout history deploy webapp  ```

```  kubectl get deploy webapp --show-labels  ```

9  ```  kubectl rollout undo deploy webapp  ```

```  kubectl describe deploy webapp | grep Image  ```

10  ```  kubectl set image deploy/webapp nginx=nginx:1.100  ```

```  kubectl rollout status deploy webapp  ```

a.  ```   kubectl get pods  ```

b.  ```  kubectl rollout undo deploy webapp  ```

```  kubectl rollout status deploy webapp  ```

```  kubectl get pods  ```

c.  ```  


