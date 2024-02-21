Upgrades - Sometimes RH blocks upgrades and you have to agree from CMDline
This won't be the CMD for future and is only an example:

To acknowledge that you have completed the evaluation and your cluster is ready to upgrade to OpenShift Container Platform 4.9, run the following command:
oc -n openshift-config patch cm admin-acks --patch '{"data":{"ack-4.8-kube-1.22-api-removals-in-4.9":"true"}}' --type=merge