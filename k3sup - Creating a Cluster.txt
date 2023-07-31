1.  Followed directions from:
https://codeberg.org/onasaft/k3sup

2.  Install K3sUp:
curl -sLS https://get.k3sup.dev | sh
sudo install k3sup /usr/local/bin/
k3sup --help

3. Setup Vars:
export SERVER1=192.168.2.101
export SERVER2=192.168.2.102
export AGENT1=192.168.2.104
export AGENT2=192.168.2.105
export USER=tom

4.  Install the first server:
k3sup install --user $USER --ip $SERVER1 --cluster

5. Test your cluster with:
scp /etc/rancher/k3s/k3s.yaml to laptop, rename k3s.yaml to ~/.kube/config, vi the config file and change the IP address
kubectl config use-context default
kubectl get node -o wide

6.  SSH into k3smast01 and get the token:
sudo cat /var/lib/rancher/k3s/server/node-token

7.  Set the token Var from the cat-ed node-token above:
export TOKEN=FillInTokenFromAbove

8.  Install the second server:
k3sup join --user tom --server-user tom --server-ip $SERVER1 --ip $SERVER2 --server

9.  Join the first agent
You can join the agent to either server.
k3sup join --user tom --server-ip $SERVER1 --ip $AGENT1

10.  Join the second agent
You can join the agent to either server.
k3sup join --user tom --server-ip $SERVER1 --ip $AGENT2

11. List nodes:
kubectl get nodes -o wide

12.  If you want to uninstall k3s or an agent:
/usr/local/bin/k3s-uninstall.sh
/usr/local/bin/k3s-agent-uninstall.sh



