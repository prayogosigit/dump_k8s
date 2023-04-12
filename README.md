# dump_k8s

INSTALL STEP BY STEP

1. 
2. sudo dpkg -i man-db_2.9.1-1_amd64.deb
3. touch /etc/modules-load.d/containerd.conf
```
5. atau " printf "overlay\nbr_netfilter" > /etc/modules-load.d/containerd.conf "
```
```
4. isi         overlay
               br_netfilter
```
6. sudo modprobe overlay
7. sudo modprobe br_netfilter
8. touch /etc/sysctl.d/99-kubernetes-cri.conf
```
atau sudo printf "net.bridge.bridge-nf-call-iptables = 1\nnet.ipv4.ip_forward = 1\nnet.bridge.bridge-nf-call-ip6tables = 1" | sudo tee -a /etc/sysctl.d/99-kubernetes-cri.conf
```
```
9. isi        net.bridge.bridge-nf-call-iptables = 1
              net.ipv4.ip_forward = 1
              net.bridge.bridge-nf-call-ip6tables = 1
```
11. sudo sysctl --system
12. sudo apt-get update && sudo apt-get install -y containerd
13. sudo mkdir -p /etc/containerd

13. sudo containerd config default | sudo tee /etc/containerd/config.toml

14. search dalam config.toml ganti "systemdCgroup = true"
atau
```
cd /etc/containerd/ && sudo sed -i '125s/false/true/g' /etc/containerd/config.toml
```
15. sudo systemctl restart containerd
16. sudo swapoff -a
17. sudo sed -i '/ swap / s/^\(.*\)$/#\1/g' /etc/fstab
18. install apt transport
19. touch /etc/apt/sources.list.d/kubernetes.list
atau
```
sudo printf "deb https://apt.kubernetes.io/ kubernetes-xenial main" | sudo tee /etc/apt/sources.list.d/kubernetes.list
```
19. isi
```
deb https://apt.kubernetes.io/ kubernetes-xenial main
```
20. sudo apt update
21. sudo dpkg -i cri-tools_1.26.0-00_amd64.deb 
22. sudo dpkg -i kubernetes-cni_1.2.0-00_amd64.deb
23. sudo dpkg -i socat_1.7.3.3-2_amd64.deb
24. sudo dpkg -i ebtables_2.0.11-3build1_amd64.deb
25. sudo dpkg -i conntrack_1%3a1.4.5-2_amd64.deb
26. sudo dpkg -i kubelet_1.26.3-00_amd64.de
27. sudo dpkg -i kubectl_1.26.3-00_amd64.deb 
28. sudo dpkg -i kubeadm_1.26.3-00_amd64.deb
29. sudo kubeadm init --pod-network-cidr=10.244.0.0/16
30. mkdir .kube mode 755
31. sudo cat /etc/kubernetes/admin.conf | sudo tee /home/azureuser/.kube/config
32. kubectl apply -f flannel.yaml
30. OPEN  PORT
![image](https://user-images.githubusercontent.com/99325356/230304394-f84cec43-a83d-4c9e-aa6f-44e10f09a3d9.png)
