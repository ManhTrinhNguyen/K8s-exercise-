#### This project is for the Devops Bootcamp Exercise for 
#### "Container Orchestration with Kubernetes" 


# Create Secret with docker config 
```
kubectl create secret docker-registry <name> \
  --docker-server=<docker-registry-server> \
  --docker-username=<docker-user> \
  --docker-password=<docker-password> \
```