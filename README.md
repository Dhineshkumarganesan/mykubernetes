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

