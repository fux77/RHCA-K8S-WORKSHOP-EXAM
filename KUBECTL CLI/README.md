1

``` kubectl run nginx-pod-boris --image=nginx:alpine ```

2

``` kubectl run messaging --image=redis:alpine --labels tier=msg ```

3

``` kubectl create ns apx-x998-boris ```

4

``` kubectl get nodes -o json >> /tmp/nodes-boris ```

5

``` kubectl create service clusterip messaging-service --tcp 6379:6379 ```

``` kubectl label svc messaging-service tier=msg ```

6

