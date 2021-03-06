1  ```  kubectl get pods --show-labels  ```

2  ```  kubectl run pod1 --image=nginx --labels=env=prod ```

   ```  kubectl run pod2 --image=nginx --labels=env=prod ```
   
   ```  kubectl run pod3 --image=nginx --labels=env=dev  ```
   
   ```  kubectl run pod4 --image=nginx --labels=env=dev  ```
   
   ```  kubectl run pod5 --image=nginx --labels=env=dev  ```

3  ```  kubeclt get pods --show-labels  ```

4  ```  kubectl get pods -l env=dev  ```

5  ```  kubectl get pods -l env=dev --show-labels  ```

6  ```  kubectl get pods -l env=prod  ```

7  ```  kubectl get pods -l env=prod --show-labels  ```

8  ```  kubectl get pods -l env  ```

9  ```  kubectl get pods -l 'env in (dev,prod)'  ```

10  ```  kubectl get pods -l 'env in (dev,prod)' --show-labels  ```

11  ```  kubectl label pods pod1 env=uat --overwrite  ```

```  kubectl get pods --show-labels  ```
    
12  ```  kubectl label pods pod{1..5} env-  ```

```  kubectl get pods --show-labels  ```

13  ```  kubectl label pods pod{1..5} app=nginx  ```

```  kubectl get pods --show-labels  ```

14  ```  kubectl get nodes --show-labels  ```

15  ```  kubectl label node ip-172-31-12-235.eu-west-1.compute.internal nodeName=nginxnode  ```

16
## nginxpod.yaml
```

apiVersion: v1
kind: Pod
metadata:
  creationTimestamp: null
  labels:
    run: nginx
  name: nginx
spec:
  nodeSelector:
    nodeName: nginxnode
  containers:
  - image: nginx
    name: nginx
    resources: {}
  dnsPolicy: ClusterFirst
  restartPolicy: Always
status: {}

```
```  kubectl apply -f nginxpod.yaml  ```

17  ```  kubectl describe pod nginx | grep Node-Selectors  ```

18  ```  kubectl describe pod nginx | grep Labels  ```
