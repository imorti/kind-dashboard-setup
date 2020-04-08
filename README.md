# Overview
This yaml can be used to install the kubernetes dashboard onto Kind or Minikube. 

# Prequesite
You have a kubernetes cluster configured and are using the proper context with `kubectl`. 

# Process
1. Run `dashboard-adminuser.yaml`
2. Run `clusterrolebinding.yaml`
3. Run `kubectl proxy`
4. Run `kubectl -n kubernetes-dashboard describe secret $(kubectl -n kubernetes-dashboard get secret | grep admin-user | awk '{print $1}')`
5. Copy the token from the output. 
6. Go to http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/
7. Select the `token` option to log in and paste the token you copied into the field. 
8. Hit sign in button and boom you're into the dashboard. 

