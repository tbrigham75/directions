For all Nodes:
for n in $(oc get nodes -o name); do echo $n; oc debug $n -- uptime; done

For all Nodes that match node-role.kubernetes.io/infra:
for n in $(oc get nodes -o name -l node-role.kubernetes.io/infra); do echo $n; oc debug $n -- uptime; done


