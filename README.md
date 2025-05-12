# mykubernetes
This is to execute the Containers: Kubernetes Cluster Administration challenge series available in Skillable through Digital Cloud Library<br><br>


kubectl describe node k8s-worker2 | grep Taints<br>

kubectl run pod_name --image=image_name label=label_name=label_name <br>

kubectl label pod pod_name label=name<br>



*******Initialize a KN cluster*******<br><br>
sudo kubeadm init --pod-network-cidr=10.244.0.0/16<br>


sudo kubeadm init --pod-network-cidr=10.244.0.0/16<br>

 open an interactive subshell<br>
sudo -i<br>


*******Install KN Cluster*******<br>

lscpu<br>
free<br>
curl -I https://kubernetes.io <br>
sudo apt-get update<br>
sudo apt-get install docker.io<br>
sudo systemctl status docker<br>
sudo systemctl enable docker<br>
sudo systemctl start docker<br>
sudo systemctl status docker<br>

--Install KN<br><br>
sudo apt-get update<br>
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add<br>
sudo apt-add-repository "deb http://apt.kubernetes.io/ kubernetes-xenial main"<br>
sudo apt-get install kubeadm kubelet kubectl<br>
sudo apt-mark hold kubeadm kubelet kubectl<br>
--Disable swap on VM<br>
free -h<br>
sudo swapoff -a<br>

sudo kubeadm init --pod-network-cidr=10.244.0.0/16 <br>

sudo nano /etc/fstab<br>
--Verify the Kubernetes and Docker component installation<br>
dpkg --get-selections | grep docker<br>
dpkg --get-selections | grep kube<br>

sudo kill -9 4814<br>
sudo rm <br>

$ mkdir -p $HOME/.kube<br>
$ sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config<br>
$ sudo chown $(id -u):$(id -g) $HOME/.kube/config<br>

sudo kubectl cluster-info<br>

sudo kubeadm join \<br>
  192.168.122.195:6443 \<br>
  --token nx1jjq.u42y27ip3bhmj8vj \<br>
  --discovery-token-ca-cert-hash sha256:c6de85f6c862c0d58cc3d10fd199064ff25c4021b6e88475822d6163a25b4a6c<br>

#kubeadm join<br>
#https://computingforgeeks.com/join-new-kubernetes-worker-node-to-existing-cluster/<br>


*******Manage KN Cluster Resources*******<br>



*******Manage KN resources*******<br>

*******Configure Services in a KN cluster*******<br>


*******Create objects in KN Cluster******* <br>

kubectl run pod1 --image=nginx <br>
kubectl label pod pod1 department=marketing <br>
kubectl run pod2 --image=nginx --labels="department=marketing" <br>
kubectl label pod pod2 division=west<br>

--Filter objects by using labels<br>
kubectl get pods --show-labels<br>
kubectl get pods --selector=department=marketing<br>
kubectl get pods -l "department=marketing,division=west"<br>
kubectl describe pod pod2<br>

--Identify objects by using a selector<br>
wget https://raw.githubusercontent.com/LODSContent/ChallengeLabs_Resources/master/CKA/webserver.deployment.yaml<br>

cat webserver.deployment.yaml<br>
kubectl create -f webserver.deployment.yaml<br>
kubectl describe deployment webserver<br>

--Annotate an Object<br>

kubectl annotate pod pod1 DevOps="do not update pod image"<br>
kubectl describe pod pod1<br>


*******Deploy a KN Cluster*******<br>

cat rs.yaml<br>
kubectl apply -f rs.yaml<br>
kubectl get replicasets<br>
kubectl delete pod <pod><br>
cat webservers.yaml<br>
kubectl apply -f webservers.yaml<br>
kubectl set image deployment webservers nginx=httpd<br>
kubectl rollout status deployment webservers<br>
kubectl describe deployment webservers<br>
kubectl scale deployment webservers --replicas=4<br>
kubectl get replicasets<br>
kubectl get pods<br>
kubectl describe deployment webservers<br>
kubectl describe deployment webservers | grep -i strategytype<br>

--Rollback deployment--<br>
kubectl rollout undo deployment webservers<br>
kubectl describe deployment webservers | grep -i image<br>

--Delete deployment<br>
kubectl delete deployment webservers<br>

kubectl cluster-info<br>
kubectl get nodes <br>
kubectl get pods <br>
kubectl get namespaces <br>
kubectl get pods --all-namespaces<br>
kubectl get nodes -o wide <br>
kubectl describe nodes<br>
kubectl describe node k8s-worker1<br>
--Retrieve information about the pods in a cluster<br>
kubectl describe nodes k8s-master1 | grep kube-system<br>
kubectl get pods kube-proxy-zrcx9 -n kube-system<br>
kubectl describe pods kube-proxy-zrcx9 -n kube-system<br>
kubectl config view <br>
kubectl get pods<br>
--Retrieve information about the cluster core components<br>
systemctl status kubelet<br>


CRITICAL INFO
*****************
Exam notes-1



Exam notes-8

Deployments provide desires state configuration for ReplicaSets.<br>
Pod domain names are of the form pod-ip-address.namespace-name.pod.cluster.local.<br>
A single NetworkPolicy can control both ingress and egress traffic.<br>
The cluster has a single virtual network spanning across all Nodes<br>
Each Pod has an IP address unique to the cluster.<br>
Scaling means changing a Deployment‘s replica count<br>
kubectl scale<br>
You can scale a deployment with this command.<br>
kubectl edit deployment<br>
You can scale a deployment by using kubectl edit to change the replica count.<br>
Rolling Updates gradually roll out changes across a Deployment‘s replicas<br>
A Deployment‘s template specifies a Pod definition used to create replicas.<br>
Rollbacks allow you to easily revert a Deployment to a previous state.<br>
DNS allows Kubernetes Pods and Servics to be located using domain names<br>
Static Pods can be used to run containers on a Node in the absence of a Kubernetes API Server<br>
nodeSelector causes the Pod to run on Nodes with specific labels.<br>
A DaemonSet would run one replica on each Node.<br>
nodeName option allows you to specify which Node the Pod should run on by name.<br>
When a new Node is added, the DaemonSet will create a replica for that Node.<br>
A Mirror Pod represents a Static Pod in the Kuberntes API, allowing you to easily view the Static Pod‘s status.<br>
You can use an init container to pause startup until an external resource becomes available.<br>
You can use an init container to do startup tasks involving sensitive data outside the main container(s).<br>
You can use an init container to populate a shared volume with data.<br>
Onfailure will ensure the container restarts if it fails, but will not be run again once it succeeds<br>
NetworkPolicies allow you to control network access to Pods.<br>
CNI plugins implement the Kubernetes Network Model in various ways.<br>
When no CNI plugin is installed, Nodes will remain in the NotReady state.<br>
Network communication between Pods is transparent, regardless of which Node(s) they are running on<br>
Ingresses expose external access to Services while providing additional features.<br>
Services provide an abstract communication layer for sets of Pods.
Endpoints are the underlying entities (such as Pods) that a Service routes traffic to.
Every Service is automatically assigned a domain name.<br>
Service domain names can be used by Pods.<br>
NodePort Services use a port on each Node to expose the Service externally.<br>
my-service.default.svc.cluster.local<br>
This is the correct fully-qualified domain name for the Service.<br>
my-service<br>
This is the short form of the domain name for the Service, which you can use because the Pod is in the same Namespace as the Service.<br>
An Ingress routes traffic to entities known as **backends**<br>
**ClusterIP** Services expose Pods to other Pods within the cluster.<br>
Container file system data is lost when the container is removed.<br>
The volume type determines the underlying storage mechanism that is used to store the data.<br>
emptyDir volume type is great for sharing data between containers, and is automatically cleaned up if the Pod is deleted.<br>
This command displays object status in a human-readable way.<br>
kubectl provides a command-line interface to the Kubernetes API<br>
etcdctl is the command-line tool for Etcd.<br>
An HA setup for Kubernetes involved **multiple control plane node**s.<br>
kubectl drain is used to **take a node down** for **maintenance**.<br>
**kubeadm upgrade apply** command will upgrade the control plane.<br>
kubectl add node will allow Pods to be scheduled on a previously-drained Node<br>
Etcd is the Backend data store or Kubernetes.<br>
**External etcd**or managing Etcd separately from other control plane components, is one option for an HA setup.<br>
**Stacked etcd**or managing Etcd alongside other control plane components, is one option for an HA setup.<br>
**kubeadm** includes functionality to help you upgrade Kubernetes clusters.<br>
Minikube allows you to easily create single-node clusters.<br>
kubeadm allows you to build Kubernetes clusters.<br>
A RoleBinding binds a Role to a subject, but only within a particular Namespace.<br>
--dry-run=client flag will validate the object, but will not actually create it.<br>
A ServiceAccount allows Pods to access the Kubernetes API.<br>
kubectl top command displays resource usage data.<br>
A ClusterRole defines a set of permission, and resides outside any Namespace.<br>
K8S The 8 stands for the 8 letters between K and S.<br>
Metrics Server tool collects data about resource usage by each container/Pod<br>
RBAC can be used to manage ServiceAccount permissions<br>
--dry-run=client flag will validate the object, but will not actually create it.<br>
 kubectl get,  --selector flag allows you to filter results by label<br>
 --record flag saves the command as an annotation on the affected object<br>
Containers within a Pod can communicate on any port.<br>
Containers within a Pod can share volumes.<br>
Startup probes run only during startup.<br>
Resource limits can prevent containers from using more resources than the limit specifies.<br>
Resource requests prevent the scheduler from scheduling Pods on Nodes that do not have enough resources to meet the request.<br>
Resource requests allow you to specify the amount of resources you expect a container to use.<br>
Liveness probes allow you to determine container status in a custom way<br>
A restart policy determines what will happen when a container stops.<br>
Secret store sensitive configuration data.<br>
A ConfigMap allows you to store key-value configuration data.<br>
Pods must have at least one container, but can have multiple containers.<br>
Init containers run before the main container(s) and perform startup tasks outside of the main container(s).<br>


Exam notes- 10<br>

kubectl provides a command-line interface to the Kubernetes API<br>
--selector flag will filter results by label.<br>
--record This flag saves the command as an annotation on the affected object.<br>
RBAC can be used to manage ServiceAccount permissions.<br>
A RoleBinding binds a Role to a subject, but only within a particular Namespace<br>
kubectl describe This command displays object status in a human-readable way.<br>
--dry-run=client This flag will validate the object, but will not actually create it<br>
kubectl top This command displays resource usage data.<br>
A Deployment‘s template specifies a Pod definition used to create replicas.<br>
Scaling means changing a Deployment‘s replica count.<br>
kubectl scale<br>
You can scale a deployment with this command<br>
 kubectl edit deployment<br>
You can scale a deployment by using kubectl edit to change the replica count.<br>
Rolling Updates gradually roll out changes across a Deployment‘s replicas.<br>
Deployments provide desires state configuration for ReplicaSets.<br>
Stacked etcd, or managing Etcd alongside other control plane components, is one option for an HA setup.<br>
External etcd, or managing Etcd separately from other control plane components, is one option for an HA setup.<br>
Metrics Server collects resource usage metrics for Pods/containers.<br>
Etcd is the Backend data store or Kubernetes.<br>
Minikube allows you to easily create single-node clusters.<br>
kubeadm allows you to build Kubernetes clusters.<br>
kubeadm upgrade apply  This command will upgrade the control plane<br>
kubectl uncordon This command will allow Pods to be scheduled on a previously-drained Node.<br>
kubectl drain is used to take a node down for maintenance.<br>
kubeadm includes functionality to help you upgrade Kubernetes clusters.<br>
An HA setup for Kubernetes involved multiple control plane nodes.<br>
etcdctl is the command-line tool for Etcd.<br>
nodeName option allows you to specify which Node the Pod should run on by name.<br>
Static Pods can be used to run containers on a Node in the absence of a Kubernetes API Server<br>
A DaemonSet would run one replica on each Node.<br>
nodeSelector causes the Pod to run on Nodes with specific labels.<br>
When a new Node is added, the DaemonSet will create a replica for that Node<br>
A Mirror Pod represents a Static Pod in the Kuberntes API, allowing you to easily view the Static Pod‘s status.<br>
Startup probes run only during startup.<br>
NetworkPolicies allow you to control network access to Pods.<br>
A single NetworkPolicy can control both ingress and egress traffic.<br>
DNS allows Kubernetes Pods and Servics to be located using domain names<br>
CNI plugins implement the Kubernetes Network Model in various ways.<br>
When no CNI plugin is installed, Nodes will remain in the NotReady state.<br>
The cluster has a single virtual network spanning across all Nodes.<br>
Each Pod has an IP address unique to the cluster.<br>
OnFailure This will ensure the container restarts if it fails, but will not be run again once it succeeds.<br>
ConfigMap A ConfigMap allows you to store key-value configuration data<br>
A restart policy determines what will happen when a container stops<br>
Pods must have at least one container, but can have multiple containers.<br>
Secret store sensitive configuration data.<br>
Resource limits can prevent containers from using more resources than the limit specifies.<br>
Shared storage volumes-Containers within a Pod can share volumes.<br>
Network ports that are not exposed to the cluster--Containers within a Pod can communicate on any port.<br>
Liveness probes allow you to determine container status in a custom way.<br>
Network communication between Pods is transparent, regardless of which Node(s) they are running on.<br>
Resource requests allow you to specify the amount of resources you expect a container to use.<br>
Resource requests prevent the scheduler from scheduling Pods on Nodes that do not have enough resources to meet the request.<br>
Init containers run before the main container(s) and perform startup tasks outside of the main container(s).<br>
You can use an init container to populate a shared volume with data<br>
You can use an init container to pause startup until an external resource becomes available.<br>
You can use an init container to do startup tasks involving sensitive data outside the main container(s).<br>
The kubectl logs command can be used to access container logs.<br>
If the Pod has more than one container, you must specify the container name.<br>
In a kubeadm cluster, cluster components such as kube-apiserver run as static Pods in the kube-system Namespace.<br>
Create a Pod and run commands inside that Pod.This is a good strategy for interacting with the Kubernetes network from within.<br>
kubectl logs -n kube-system --In a kubeadm cluster, kube-apiserver runs as a system pod. Therefore, you can get the logs with the kubectl logs command<br>
Look for DNS Pods in the kube-system Namespace--In a kubeadm cluster, the DNS runs as Pods within the kube-system Namespace.<br>
kubectl get nodes - This command will display all Nodes, along with their status.<br>
kubectl describe pod kubectl describe displays detailed status information in a human-readable way.<br>
sudo journalctl -u kubelet In a kubeadm cluster, kubelet runs as a standard service. Therefore, you can view its logs with journalctl.<br>
kubectl exec -n dev my-pod -c busybox -- ls This command includes all elements necessary to execute the command in the correct container.<br>
kubectl logs This command can be used to obtain container logs.<br>
ClusterRole A ClusterRole defines a set of permission, and resides outside any Namespace.<br>




 
docker stuff<br>
docker<br>
containerd (process supervisor)<br>
docker swarm (orchestration)<br>
<br>
Kubernetes stuff<br>
kubernetes (orchestration, has many components)

Mesosphere stuff<br>
Mesos (orchestration)<br>

CoreOS stuff<br>
CoreOS (linux distribution)<br>
rkt (runs containers)<br>
flannel (network overlay)<br>
etcd (key-value store)<br>

HashiCorp stuff<br>
consul (key-value store, service discovery)<br>
packer (creates containers)<br>
vault (secrets management)<br>
nomad (orchestration)<br>

OCI (open container initiative) stuff<br>
runC (runs containers)<br>
libcontainer (donated by Docker, powers runC)<br>
systemd-nspawn (man page) (starts containers)<br>
dumb-init (init process)<br>
LXC (runs containers, from Canonical)<br>
 



Storage Drivers

![image](https://github.com/user-attachments/assets/dc221c7b-17f3-4b51-ad29-53b07576fbb4)

Container Storage Driver

![image](https://github.com/user-attachments/assets/b0fa4437-b3cc-475d-b9bd-3307cd5ef55c)


Volumes

![image](https://github.com/user-attachments/assets/6e7fbf4c-2797-48ee-a562-163d16351eb2)

![image](https://github.com/user-attachments/assets/bd307466-d78a-4bd3-b6fc-d8f6365349f4)

![image](https://github.com/user-attachments/assets/16b8bde4-4583-4199-9088-5fc58889190d)

![image](https://github.com/user-attachments/assets/6e89a586-84a9-42c6-b4e5-d2508ac5f57f)

![image](https://github.com/user-attachments/assets/74f2a598-08ff-452b-8fef-82aef9f8be7e)





![image](https://github.com/user-attachments/assets/98a2cc2b-8874-49f5-ac99-75ab7b151996)

![image](https://github.com/user-attachments/assets/14ec01ae-5c54-4510-bc23-08157dedf28c)


![image](https://github.com/user-attachments/assets/78a160df-974f-4c37-aac6-4239311e03d7)



