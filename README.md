# kubernetespractice
Templates to work on kubernetes & Here in below listing most useful commands and those uses


***Kubernetes***

***Nodes (or) minions***
A Cluster is a set of nodes (Mater & Worker Nodes)
Components—> API, etc, kubelet(agent), Container runtime, Scheduler, Controller.
Command line utility kubectl,  kube command line, or tube control.
kubectl run command is used to deploy an application on the cluster .
The “kubectl cluster-info” command is used to view information about the cluster.
Minikube——> VirtualBox(hypervisor)
Is a iso image
kubectl get nodes
kubectl get nodes -o wide
kubectl run nginx —image=nginx
kubectl get pods
kubectl describe nginx
kubectl apply -f pod.yaml
kubectl describe pod nginx
kubectl edit pod nginx
Pod definition file

***Replication Controller and ReplicaSets:***
  - Replication Controller is older technology that is replaced by replicates, replica set is new recommendation to set replication
kubectl create -f rc-definition.yaml
kubectl get replication controller
kubectl get pods

***Replica Set:***
kubectl create -f replicates-definition.yaml
kubectl get replicates
kubectl get pods

***Labels & Selectors:***
***Scale:***
kubectl replace -f replicaset-definition.yaml (or)
kubectl scale —replica=6 -f replicates-definition.yaml (or)(this will not change in definition file)
kubectl scale —replica=6 -f replicates myapp-replicaset

***Deployments:***
kubectl create -f deployment.yaml
kubetctl get deployments
kubectl get all
kubectl describe deployment my app-deployment

***Rollout and  Versioning***
Rollout Commands
kubectl rollout status deployment/myapp-deployment
kubectl rollout history deployment/myapp-deployment
Rollback
kubectl rollout undo deployment/myapp-deployment

***Deployment Strategy***
Recreate startegy,  Rolling Update(default)

***Kubectl apply***
kubectl apply -f deployment-definition.yml (or)
kubectl set image deployment/myapp-deployment \ nginx=nginx:1.9.1

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
kubectl get services
kubectl describe service kubernetes
Default Service is ClusterIP
Loadbalancers like Jproxy or nginx
