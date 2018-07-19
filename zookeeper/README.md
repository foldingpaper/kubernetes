Zookeeper on minikube
====

Pre-requisites
----
# minikube
# zookeeper-deployment.yaml

Steps
----


# Deploy the suite
```
kubectl apply -f zookeeper.yaml
```
# Verify 
```
kubectl get pods -w -l app=zk
```
# Sanity check
```
kubectl exec zk-0 zkCli.sh create /hello world
kubectl exec zk-1 zkCli.sh get /hello
```

Clean up
----

# kubectl delete statefulset zk
