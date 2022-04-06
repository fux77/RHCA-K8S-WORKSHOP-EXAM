1   ``` kubectl run nginx-pod-boris --image=nginx:alpine ```

2   ``` kubectl run messaging --image=redis:alpine --labels tier=msg ```

3   ``` kubectl create ns apx-x998-boris ```

4   ``` kubectl get nodes -o json > /tmp/nodes-boris ```

5   ``` kubectl expose pod messaging --name=messaging-service --port 6379 ```

6
## messaging-service.yaml

```
apiVersion: v1
kind: Service
metadata:
  name: messaging-service
  labels:
    tier: msg
spec:
  ports:
    - protocol: TCP
      port: 6379
      targetPort: 6379
  selector:
    tier: msg
```
      
``` kubectl apply -f messaging-service.yaml ```

7 
## hr-web-app.yaml

```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: hr-web-app
  labels:
    app: hr-web
spec:
  replicas: 2
  selector:
    matchLabels:
      app: hr-web
  template:
    metadata:
      labels:
        app: hr-web
    spec:
      containers:
        - name: kodekloud
          image: kodekloud/webapp-color
```         
``` kubectl apply -f hr-web-app.yaml ```

8
## static-busybox.yaml

```

apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: null
  labels:
    run: static-busybox
  name: static-busybox
spec:
  containers:
  - command: ["sleep", "1000"]
    image: busybox
    name: static-busybox
    resources: {}
  nodeSelector:
    kubernetes.io/hostname: ip-172-31-15-15.eu-west-1.compute.internal      
  dnsPolicy: ClusterFirst
  restartPolicy: Always
status: {}

```

```  kubectl apply -f static-busybox.yaml  ```

9
## temp-bus.yaml

```

apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: null
  labels:
    run: temp-bus
  name: temp-bus
  namespace: finance-boris
spec:
  containers:
  - image: redis:alpine
    name: temp-bus
    resources: {}
  dnsPolicy: ClusterFirst
  restartPolicy: Never
status: {}

```

```  kubectl create namespace finance-boris  ```

```  kubectl apply -f temp-bus.yaml  ```

10
## pv-analytics.yaml

```

apiVersion: v1
kind: PersistentVolume
metadata:
  name: pv-analytics
spec:  
  capacity:    
    storage: 100Mi  
  accessModes:    
    - ReadWriteMany  
  hostPath:    
    path: /pv/data-analytics
    
 ```
 
 ``` kubectl apply -f pv-analytics.yaml  ```
 
 11
 ## redis-storage-boris.yaml
 
 ```
 
 apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: null
  labels:
    run: redis-storage-boris
  name: redis-storage-boris
spec:
  containers:
  - image: redis:alpine
    name: redis-storage-boris    
    volumeMounts:    
    - mountPath: /data/redis
      name: cache-volume  
  volumes:  
  - name: cache-volume
    emptyDir: {}
    
    ```
    
 ```  kubectl apply -f redis-storage-boris.yaml  ```
 
 


