Targil 1

kubectl run nginx-pod-boris --image=nginx:alpine ```

Targil 2

kubectl run messaging --image=redis:alpine --labels tier=msg ```

Targil 3

kubectl create ns apx-x998-boris ```

Targil 4

kubectl get nodes -o json >> /tmp/nodes-boris ```

Targil 5
kubectl create service clusterip messaging-service --tcp 6379:6379 ```
kubectl label svc messaging-service tier=msg ```




