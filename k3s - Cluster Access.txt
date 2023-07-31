https://docs.k3s.io/cluster-access

1. SCP /etc/rancher/k3s/k3s.yaml from a node on your cluster
2.  Change the 127.0.0.1 address to a node
3.  Rename k3s.yaml to config and put into ~/.kube/