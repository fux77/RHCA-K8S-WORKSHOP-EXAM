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

7   ``` kubectl create deploy hr-web-app --image kodekloud/webapp-color --replicas=2 ```

8   ``` 

