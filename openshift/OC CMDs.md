oc get mcp - Machine Config Pool
oc get nodes
oc config current-context
oc delete pod podname --force --grace-period=0
oc get groups|grep fillinusername
oc get projects --as=fillinusername --as-group=fillingroupname
oc get ns -o yaml | grep filleinsearchterm
oc delete project fillinprojectname --force --grace-period=0
oc get po -o wide

oc get all doesn't get everything such as secrets or build configs.

This will get all info:
oc api-resources --verbs=list --namespaced -o name | xargs -n 1 oc get --show-kind --ignore-not-found -n ti-build