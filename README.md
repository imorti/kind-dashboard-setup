# Overview
This yaml can be used to install the kubernetes dashboard onto Kind or Minikube. 

# Prequesite
You have a kubernetes cluster configured and are using the proper context with `kubectl`. 

# Process
1. Install `kind` by running `brew install kind`. 
2. Create cluster by running `kind create cluster`. 
3. Check kubernetes config by running `kubectl get nodes -o wide`. You should see some output like this: 
![alt text](kind-ready.png)
4. Now let's apply the Dashboard. Run `kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.0-beta8/aio/deploy/recommended.yaml`
5. Run `kubectl apply -f dashboard-adminuser.yaml`
6. Run `kubectl apply -f clusterrolebinding.yaml`
7. Run `kubectl proxy`
8. Run `kubectl -n kubernetes-dashboard describe secret $(kubectl -n kubernetes-dashboard get secret | grep admin-user | awk '{print $1}')`
9.  Copy the token from the output. 
10. Go to http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/
11. Select the `token` option to log in and paste the token you copied into the field. 
12. Hit sign in button and boom you're into the dashboard. 

