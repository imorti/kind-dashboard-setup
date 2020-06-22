# Overview
This yaml can be used to install the kubernetes dashboard onto Kind or Minikube. 

# Prequesite
You have a kubernetes cluster configured and are using the proper context with `kubectl`. 

# Process
1. Run `kind create cluster --name <name of cluster> --config config.yaml`
2. Run `kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.0-beta8/aio/deploy/recommended.yaml`
3. Run `kubectl apply -f dashboard-adminuser.yaml`
4. Run `kubectl apply -f clusterrolebinding.yaml`
5. Run `kubectl proxy`
6. Run `kubectl -n kubernetes-dashboard describe secret $(kubectl -n kubernetes-dashboard get secret | grep admin-user | awk '{print $1}')`
7. Copy the token from the output. 
8. Go to http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/
9. Select the `token` option to log in and paste the token you copied into the field. 
10. Hit sign in button and boom you're into the dashboard. 

