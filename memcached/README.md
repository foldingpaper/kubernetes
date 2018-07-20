Memcached on minikube
====

Pre-requisites
----

1. minikube
2. helm


Steps
----

1. add bitnami repo
```
helm repo add bitnami https://charts.bitnami.com/bitnami
```
2. install memcached
```
helm install bitnami/memcached
...
...
...
Memcached can be accessed on port 11211 on the following DNS name from within your cluster: coiling-elephant-memcach.default.svc.cluster.local
```
3. telnet into the fqdn as follows:
```
kubectl run -it --rm alpine --image=alpine:3.6 --restart=Never telnet coiling-elephant-memcach.default.svc.cluster.local 11211
```
4.
```
set mykey 0 0 5
hello
STORED
get mykey
VALUE mykey 0 5
hello
END
quit
```
5. cleanup
```
help list
helm delete coiling-elephant
```
