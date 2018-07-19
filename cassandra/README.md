Cassandra cluster on minikube -- Quick steps
====

Pre-requisites
----

1. minikube
2. cassandra-service.yaml and cassandra-statefulset.yaml

Start minikube
----
1. minikube start --memory 5120 --cpus=4

Cassandra
----

1. kubectl create -f cassandra-service.yaml
2. kubectl get svc cassandra
3. kubectl create -f cassandra-statefulset.yaml
4. kubectl get statefulset cassandra
5. kubectl get pods -l="app=cassandra"
6. kubectl exec cassandra-0 -- nodetool status

Scale Cassandra
----
1. kubectl edit statefulset cassandra
2. update the replicas from 3 to 4
3. kubectl get statefulset cassandra

Clean up
----
1. Delete statefulsets
```
grace=$(kubectl get po cassandra-0 -o=jsonpath='{.spec.terminationGracePeriodSeconds}') \
     && kubectl delete statefulset -l app=cassandra \
     && echo "Sleeping $grace" \
     && sleep $grace \
     && kubectl delete pvc -l app=cassandra
```

2. Delete service
```
kubectl delete service -l app=cassandra
```


Reference
----

* https://kubernetes.io/docs/tutorials/stateful-application/cassandra/
