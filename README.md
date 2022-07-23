# k8s-in-action
## Kubernetes in action notes

## Chapter 01

### Master node vs worker node

master node components
- etcd a distributed key value store
- kube apiserver
    - kubectl proxy —port=8080
- kube controller manager
- kube scheduler
    - kubetcl get pods -n kube-system

### Woker node components
- kubelet
- container runtime
- kube-proxy
    - DaemonSet: one instance up and running on every node
    - kubectl get daemonsets -n kube-system

### Pod
- kubectl create -f <yaml>
- kubectl apply  -f <yaml>
- kubectl get pod <name>
- kubectl delete pod <name>

### ReplicaSet
- a replica is an exact copy of the same pod
- makes sure k8s runs desired number of replica of podkubectl get rs <name replicaset> 

### Deployment
	
	kubectl get deployment <name replicaset>

	kubectl rollout history deploy <name deployment> // check history of deployment
	
	kubectl rollout undo deployment <name deployment> --to-revision=<id>

- Default revision history is 10. We can set number of history by **revisionHistoryLimit**


### Job 

### Service
Service type
- ClusterIP
- NodePort
- LoadBalancer (Range 30000 - 32767)
- Headless (none)

	kubectl get pods -o wide  - get list of pods
	kubectl logs <pod name>

    NodePort
	-> expose webserver to outside
	minikube service webserver 

	
### Ingress
	reverse proxy routes the request from single server to internal
	minikube ip 

### Persistent Volume (PV) 
	an abstraction of data volume

    Persistent Volume Claim
	    bind to PV

### ConfigMaps
Resoure type `ConfigMap`

A ConfigMap allow us to store data in terms of key-value pairs or files. it can be mapped into our pods just like PVC
### Secrets
Resoucre name: Secret

Secrets will be stored securely and cannot be read by unauthorized parties.

Define the contains of data as base64 encoded strings

	
	kubectl create secret generic <secret_name> [--from-literal=<key-value>]

	kubectl get secret <secret_name> -o yaml


### Namespaces

a separate space for differentating resource names

    kubectl create ns <namespace name>

    kubectl get ns

ConfigMap or Secret can not be shared betwwen Namespaces

### NetworkPolicies
resource to define firewall rules on the network layer for communication between Pods
### DaemonSet
A set of Pods rolled out on each kubernetes node
- One node has 1 pod daemonset
- Using for monitoring or logging
### CronJobs
Similar to Jobs and schaduled via cron expression
### StatefulSets
Resource similar to ReplicaSets

## Chapter 02

Deployment logs

	kubectl logs deployments/<deployment_name> -n <namespace>

	kubectl -n <namespace> describe pods <pod_name>

## Chapter 03

Dev-to-K8s

	A. Local development – Execution on Kubernetes
	B. Local development – Hybrid execution
	C. Development on Kubernetes – Execution on Kubernetes

Helm chart
	
	test

## Chapter 04

RESTful Kubenetes API

	Return list Pods of Resource type
	<protocol://hostname:port>/apis/GROUP/VERSION/RESOURCETYPE

	Return list Pods of Resource type in specific Namespace
	<protocol://hostname:port>/apis/GROUP/VERSION/namespaces/NAMESPACE/RESOURCETYPE

	Return the resource in the given Namespace with the given name
	<protocol://hostname:port>/apis/GROUP/VERSION/ 
	namespaces/NAMESPACE/RESOURCETYPE/NAME
	
Downward API


