Environment AWS with EC2

1. run install-kubeadm.sh
2. kubeadm init --pod-network-cidr=10.244.0.0/16 --control-plane-endpoint=your-ip-public-master-node
3. Joint the worker node
4. mkdir -p $HOME/.kube; sudo cp -i /etc/kubernetes/admin.conf $HOME/.kube/config; sudo chown $(id -u):$(id -g) $HOME/.kube/config
5. kubectl apply -f https://raw.githubusercontent.com/coreos/flannel/master/Documentation/kube-flannel.yml

If you want to use another network cidr pod, adjust the network cidr pod in kube-flannel.yml

Environment LXC

mknod /dev/kmsg c 1 11
echo 'mknod /dev/kmsg c 1 11' >> /etc/rc.local
chmod +x /etc/rc.local

kubeadm init --pod-network-cidr=10.244.0.0/16 --ignore-preflight-errors=all --control-plane-endpoint=your-ip-public-master-node

 
