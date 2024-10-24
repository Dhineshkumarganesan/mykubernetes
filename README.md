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
Exam -8

Deployments provide desires state configuration for ReplicaSets.<br>
Pod domain names are of the form pod-ip-address.namespace-name.pod.cluster.local.<br>
A single NetworkPolicy can control both ingress and egress traffic.<br>
The cluster has a single virtual network spanning across all Nodes<br>
Each Pod has an IP address unique to the cluster.<br>
Scaling means changing a Deployment‘s replica count
kubectl scale
You can scale a deployment with this command.
kubectl edit deployment
You can scale a deployment by using kubectl edit to change the replica count.
Rolling Updates gradually roll out changes across a Deployment‘s replicas
A Deployment‘s template specifies a Pod definition used to create replicas.
Rollbacks allow you to easily revert a Deployment to a previous state.
DNS allows Kubernetes Pods and Servics to be located using domain names
Static Pods can be used to run containers on a Node in the absence of a Kubernetes API Server
nodeSelector causes the Pod to run on Nodes with specific labels.
A DaemonSet would run one replica on each Node.
nodeName option allows you to specify which Node the Pod should run on by name.
When a new Node is added, the DaemonSet will create a replica for that Node.
A Mirror Pod represents a Static Pod in the Kuberntes API, allowing you to easily view the Static Pod‘s status.
You can use an init container to pause startup until an external resource becomes available.
You can use an init container to do startup tasks involving sensitive data outside the main container(s).
You can use an init container to populate a shared volume with data
Onfailure will ensure the container restarts if it fails, but will not be run again once it succeeds
NetworkPolicies allow you to control network access to Pods.
CNI plugins implement the Kubernetes Network Model in various ways.
When no CNI plugin is installed, Nodes will remain in the NotReady state.
Network communication between Pods is transparent, regardless of which Node(s) they are running on
Ingresses expose external access to Services while providing additional features.
Services provide an abstract communication layer for sets of Pods.
Endpoints are the underlying entities (such as Pods) that a Service routes traffic to.
Every Service is automatically assigned a domain name.
Service domain names can be used by Pods.
NodePort Services use a port on each Node to expose the Service externally.
my-service.default.svc.cluster.local
This is the correct fully-qualified domain name for the Service.
my-service
This is the short form of the domain name for the Service, which you can use because the Pod is in the same Namespace as the Service.
An Ingress routes traffic to entities known as **backends**
**ClusterIP** Services expose Pods to other Pods within the cluster.
Container file system data is lost when the container is removed.
The volume type determines the underlying storage mechanism that is used to store the data.
emptyDir volume type is great for sharing data between containers, and is automatically cleaned up if the Pod is deleted.
This command displays object status in a human-readable way.
kubectl provides a command-line interface to the Kubernetes API
etcdctl is the command-line tool for Etcd.
An HA setup for Kubernetes involved **multiple control plane node**s.
kubectl drain is used to **take a node down** for **maintenance**.
**kubeadm upgrade apply** command will upgrade the control plane.
kubectl add node will allow Pods to be scheduled on a previously-drained Node
Etcd is the Backend data store or Kubernetes.
**External etcd**or managing Etcd separately from other control plane components, is one option for an HA setup.
**Stacked etcd**or managing Etcd alongside other control plane components, is one option for an HA setup.
**kubeadm** includes functionality to help you upgrade Kubernetes clusters.
Minikube allows you to easily create single-node clusters.
kubeadm allows you to build Kubernetes clusters.
A RoleBinding binds a Role to a subject, but only within a particular Namespace.
--dry-run=client flag will validate the object, but will not actually create it.
A ServiceAccount allows Pods to access the Kubernetes API.
kubectl top command displays resource usage data.
A ClusterRole defines a set of permission, and resides outside any Namespace.
K8S The 8 stands for the 8 letters between K and S.
Metrics Server tool collects data about resource usage by each container/Pod
RBAC can be used to manage ServiceAccount permissions
--dry-run=client flag will validate the object, but will not actually create it.
 kubectl get,  --selector flag allows you to filter results by label
 --record flag saves the command as an annotation on the affected object
Containers within a Pod can communicate on any port.
Containers within a Pod can share volumes.







