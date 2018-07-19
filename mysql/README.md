Mysql on minikube
====

Pre-requisites
----
# minikube
# mysql-deployment.yaml

Steps
----

# Create secret
```
kubectl create secret generic mysql-pass --from-literal=password=YOUR_PASSWORD
```
# Verify
```
kubectl get secrets
```
# Deploy mysql
```
kubectl create -f https://k8s.io/examples/application/wordpress/mysql-deployment.yaml
```
# Verify PVs
```
kubectl get pvc
```
# Verify mysql
```
kubectl get pods
```

Clean up
----

# kubectl delete secret mysql-pass
# kubectl delete deployment -l app=fooapp
# kubectl delete service -l app=fooapp
# kubectl delete pvc -l app=fooapp
