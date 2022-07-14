# k8s-in-action
## Kubernetes in action notes

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
	kubectl rollout undo deployment <name deployment> 

### Job 

### Service
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
