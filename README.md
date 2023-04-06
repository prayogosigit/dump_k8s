# dump_k8s

INSTALL STEP BY STEP

1. 
2. dpkg -i man-db
3. touch /etc/modules-load.d/containerd.conf
```
4. isi         overlay
               br_netfilter
```
6. sudo modprobe overlay
7. sudo modprobe br_netfilter
8. touch /etc/sysctl.d/99-kubernetes-cri.conf
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
15. sudo systemctl restart containerd
16. sudo swapoff -a
17. sudo sed -i '/ swap / s/^\(.*\)$/#\1/g' /etc/fstab
18. install apt transport
19. touch /etc/apt/sources.list.d/kubernetes.list
```
19. isi          deb https://apt.kubernetes.io/ kubernetes-xenial main
```
20. sudo apt update
21. dpkg -i cri-tools
22. dpkg -i kubernetes_cni
23. dpkg -i socat
24. dpkg -i ebtables
25. dpkg -i conntrack
26. dpkg -i kubelet
27. dpkg -i kubeadm
28. dpkg -i kubectl
29. OPEN  PORT
![image](https://user-images.githubusercontent.com/99325356/230304394-f84cec43-a83d-4c9e-aa6f-44e10f09a3d9.png)
