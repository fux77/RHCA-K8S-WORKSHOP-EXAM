1
## config.txt

```

key1=value1
key2=value2

```

2  ```  kubectl create cm keyvalcfgmap --from-file=config.txt  ```

```  kubectl get cm keyvalcfgmap -o yaml  ```

3
## nginx-pod.yml

```

apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: null
  labels:
    run: nginx
  name: nginx
spec:
  containers:
  - image: nginx
    name: nginx
    resources: {}
    envFrom:
    - configMapRef:
        name: keyvalcfgmap
  dnsPolicy: ClusterFirst
  restartPolicy: Never
status: {}

```

```  kubectl apply -f nginx-pod.yml  ```

```  kubectl exec -it nginx -- env  ```

```  kubectl delete pod nginx  ```
