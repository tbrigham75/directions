1. It starts with a Node Label.  Can be seen under Compute > Nodes > Node labels.  Example:  cluster.ocs.openshift.io/openshift-storage

2. Taint is on same page as above:
Key				Value	Effect
node.ocs.openshift.io/storage 	True	NoSchedule

3.  Every pod running on Node (In YAML) will have a Toleration that matches Taint:
tolerations:
  - key: node.ocs.openshift.io/storage
    operator: Equal
    value: 'true'
    effect: NoSchedule
4.  If Pod doesn't have a matching toleration it will not be considered for scheduling on that node.  So only things running on storage nodes will be core services like log collectors, network infrastructure, and storage workloads.

5.  nodeSelectors also play their role in this, by the below YAML it will only consider linux nodes and must have infra label:

spec:
  nodeSelector:
    kubernetes.io/os: linux
    node-role.kubernetes.io/infra: ''

6.  Resources are also determined and if it ask for a certain amount it will find a node that can run the pod.