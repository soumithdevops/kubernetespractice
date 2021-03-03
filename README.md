# kubernetespractice
Templates to work on kubernetes & Here in below listing most useful commands and those uses


***Kubernetes***

***Nodes (or) minions***
A Cluster is a set of nodes (Mater & Worker Nodes)
Components—> API, etc, kubelet(agent), Container runtime, Scheduler, Controller.
Command line utility kubectl,  kube command line, or tube control.
Kubectl run command is used to deploy an application on the cluster .
The “kubectl cluster-info” command is used to view information about the cluster.
Minikube——> VirtualBox(hypervisor)
Is a iso image
kubectl get nodes
kubectl get nodes -o wide
Kubectl run nginx —image=nginx
Kubectl get pods
Kubectl describe nginx
Kubectl apply -f pod.yaml
Kubectl describe pod nginx
Kubectl edit pod nginx
Pod definition file

***Replication Controller and ReplicaSets:***
  - Replication Controller is older technology that is replaced by replicates, replica set is new recommendation to set replication
Kubectl create -f rc-definition.yaml
Kubectl get replication controller
Kubectl get pods

***Replica Set:***
Kubectl create -f replicates-definition.yaml
Kubectl get replicates
Kubectl get pods

***Labels & Selectors:***
***Scale:***
Kubectl replace -f replicaset-definition.yaml (or)
Kubectl scale —replica=6 -f replicates-definition.yaml (or)(this will not change in definition file)
Kubectl scale —replica=6 -f replicates myapp-replicaset

***Deployments:***
Kubectl create -f deployment.yaml
Kubetctl get deployments
Kubectl get all
Kubectl describe deployment my app-deployment

***Rollout and  Versioning***
Rollout Commands
Kubectl rollout status deployment/myapp-deployment
Kubectl rollout history deployment/myapp-deployment
Rollback
Kubectl rollout undo deployment/myapp-deployment

***Deployment Strategy***
Recreate startegy,  Rolling Update(default)

***Kubectl apply***
Kubectl apply -f deployment-definition.yml (or)
Kubectl set image deployment/myapp-deployment \ nginx=nginx:1.9.1

***Record change-cause***
 kubectl create -f deployment.yaml --record
 kubectl rollout history deployment/myapp-deployment

***Networking in Kubernetes***
IP address is assigned to a POD (Ex: 10.244.0.2)
Internal private network address is created when kuberenets is initially configured on each node.
Cluster Networking
Routing techniques(NSX,vmware,cilium,flannel & cisco)

***Services -*** 
Kubernetes services helps us connect applications together with other applications or users

***NodePort, clusterIP, LoadBalancer*** 
Nodeport- 30000 to 32767 (port on a node to pod)
clusterIP- Services creates virtual IP inside cluster to enable communication between services such as set of front end servers to backend servers
Loadbalancer-  Where it provisions a load balancer for our application in supported cloud providers
TargetPort(pod port)—>port(Service port)——>Nodeport(port on node)
List services
Kubectl get services
kubectl describe service kubernetes
Default Service is ClusterIP
Loadbalcers like Jproxy or nginx
