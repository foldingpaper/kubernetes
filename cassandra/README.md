Cassandra cluster on minikube -- Quick steps
====

Pre-requisites
----

# minikube
# cassandra-service.yaml and cassandra-statefulset.yaml

Start minikube
----
# minikube start --memory 5120 --cpus=4

Cassandra
----

# kubectl create -f https://k8s.io/examples/application/cassandra/cassandra-service.yaml
# kubectl get svc cassandra
# kubectl create -f https://k8s.io/examples/application/cassandra/cassandra-statefulset.yaml
# kubectl get statefulset cassandra
#  kubectl get pods -l="app=cassandra"
# kubectl exec cassandra-0 -- nodetool status

Scale Cassandra
----
# kubectl edit statefulset cassandra
# update the replicas from 3 to 4
# kubectl get statefulset cassandra

Clean up
----
# grace=$(kubectl get po cassandra-0 -o=jsonpath='{.spec.terminationGracePeriodSeconds}') \
     && kubectl delete statefulset -l app=cassandra \
     && echo "Sleeping $grace" \
     && sleep $grace \
     && kubectl delete pvc -l app=cassandra

# kubectl delete service -l app=cassandra

Reference
----

* https://kubernetes.io/docs/tutorials/stateful-application/cassandra/
