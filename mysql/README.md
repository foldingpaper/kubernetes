Mysql on minikube
====

Pre-requisites
----
* minikube
* mysql-deployment.yaml

Steps
----

1. Create secret
```
kubectl create secret generic mysql-pass --from-literal=password=YOUR_PASSWORD
```
2. Verify
```
kubectl get secrets
```
3. Deploy mysql
```
kubectl create -f https://k8s.io/examples/application/wordpress/mysql-deployment.yaml
```
4. Verify PVs
```
kubectl get pvc
```
5. Verify mysql
```
kubectl get pods
```

Clean up
----

* kubectl delete secret mysql-pass
* kubectl delete deployment -l app=fooapp
* kubectl delete service -l app=fooapp
* kubectl delete pvc -l app=fooapp
