# mykubernetes
This is to execute the Containers: Kubernetes Cluster Administration challenge series available in Skillable through Digital Cloud Library


kubectl describe node k8s-worker2 | grep Taints

kubectl run pod_name --image=image_name label=label_name=label_name 

kubectl label pod pod_name label=name



*******Initialize a KN cluster*******
sudo kubeadm init --pod-network-cidr=10.244.0.0/16


sudo kubeadm init --pod-network-cidr=10.244.0.0/16

 open an interactive subshell
sudo -i


*******Install KN Cluster*******

lscpu
free
curl -I https://kubernetes.io 
sudo apt-get update
sudo apt-get install docker.io
sudo systemctl status docker
sudo systemctl enable docker
sudo systemctl start docker
sudo systemctl status docker

--Install KN
sudo apt-get update
curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add
sudo apt-add-repository "deb http://apt.kubernetes.io/ kubernetes-xenial main"
sudo apt-get install kubeadm kubelet kubectl
sudo apt-mark hold kubeadm kubelet kubectl
--Disable swap on VM
free -h
sudo swapoff -a

sudo kubeadm init --pod-network-cidr=10.244.0.0/16 

sudo nano /etc/fstab
--Verify the Kubernetes and Docker component installation
dpkg --get-selections | grep docker
dpkg --get-selections | grep kube

sudo kill -9 4814
sudo rm 

$ mkdir -p $HOME/.kube
$ sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config
$ sudo chown $(id -u):$(id -g) $HOME/.kube/config

sudo kubectl cluster-info

sudo kubeadm join \
  192.168.122.195:6443 \
  --token nx1jjq.u42y27ip3bhmj8vj \
  --discovery-token-ca-cert-hash sha256:c6de85f6c862c0d58cc3d10fd199064ff25c4021b6e88475822d6163a25b4a6c

kubeadm join
https://computingforgeeks.com/join-new-kubernetes-worker-node-to-existing-cluster/


*******Manage KN Cluster Resources*******



*******Manage KN resources*******

*******Configure Services in a KN cluster*******


*******Create objects in KN Cluster******* 

kubectl run pod1 --image=nginx
kubectl label pod pod1 department=marketing
kubectl run pod2 --image=nginx --labels="department=marketing"
kubectl label pod pod2 division=west

--Filter objects by using labels
kubectl get pods --show-labels
kubectl get pods --selector=department=marketing
kubectl get pods -l "department=marketing,division=west"
kubectl describe pod pod2

--Identify objects by using a selector
wget https://raw.githubusercontent.com/LODSContent/ChallengeLabs_Resources/master/CKA/webserver.deployment.yaml

cat webserver.deployment.yaml
kubectl create -f webserver.deployment.yaml
kubectl describe deployment webserver

--Annotate an Object

kubectl annotate pod pod1 DevOps="do not update pod image"
kubectl describe pod pod1


*******Deploy a KN Cluster*******

cat rs.yaml
kubectl apply -f rs.yaml
kubectl get replicasets
kubectl delete pod <pod>
cat webservers.yaml
kubectl apply -f webservers.yaml
kubectl set image deployment webservers nginx=httpd
kubectl rollout status deployment webservers
kubectl describe deployment webservers
kubectl scale deployment webservers --replicas=4
kubectl get replicasets
kubectl get pods
kubectl describe deployment webservers
kubectl describe deployment webservers | grep -i strategytype

--Rollback deployment--
kubectl rollout undo deployment webservers
kubectl describe deployment webservers | grep -i image

--Delete deployment
kubectl delete deployment webservers

kubectl cluster-info
kubectl get nodes 
kubectl get pods
kubectl get namespaces
kubectl get pods --all-namespaces
kubectl get nodes -o wide 
kubectl describe nodes
kubectl describe node k8s-worker1
--Retrieve information about the pods in a cluster
kubectl describe nodes k8s-master1 | grep kube-system
kubectl get pods kube-proxy-zrcx9 -n kube-system
kubectl describe pods kube-proxy-zrcx9 -n kube-system
kubectl config view 
kubectl get pods
--Retrieve information about the cluster core components
systemctl status kubelet
