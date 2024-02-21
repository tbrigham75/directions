Gets all nodes:
oc get nodes -o name | wc -l

Gets all Infra
oc get nodes -o name -l node-role.kubernetes.io/infra | wc -l