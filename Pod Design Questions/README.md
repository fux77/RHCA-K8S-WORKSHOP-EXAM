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
    
12  ```      
