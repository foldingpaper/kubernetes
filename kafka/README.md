Kafka on minikube
====

Pre-requisites
----
1. minikube
2. zk and kafka manifest files

Steps
----

1. Kafka needs Zookeeper
```
kubectl apply -f ./zookeeper
```
2. Deploy kafka
```
kubectl apply -f ./kafka
```

Clean up
----

1. 
