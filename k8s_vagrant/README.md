# k8s_vagrant
## Virtualbox
https://www.virtualbox.org/wiki/Downloads

## Install vagrant 
```
sudo apt update && sudo apt install vagrant
```

## Init Node Image
```
vagrant init hashicorp/bionic64
vagrant box add hashicorp/bionic64
vagrant box remove hashicorp/bionic64
vagrant box list
```

## VM start
```
vagrant up
vagrant up --provider=virtualbox
vagrant list
```

# Current VM status
```
vagrant status
vagrant ssh master
vagrant ssh worker1
vagrant ssh worker2
```

# Add K8S WorkerNode to K8S ControlPlane(Master) Node
```
cat join.sh
vagrant ssh worker1 -c "sudo kubeadm join 192.168.56.10:6443 --token <RANDOM_STRING> --discovery-token-ca-cert-hash sha256:<RANDOM_STRING>"
vagrant ssh worker2 -c "sudo kubeadm join 192.168.56.10:6443 --token <RANDOM_STRING> --discovery-token-ca-cert-hash sha256:<RANDOM_STRING>"
```

# Stop VM
```
vagrant halt
```

# remove VM
```
vagrant destory worker2
vagrant destory worker1
vagrant destory master

```