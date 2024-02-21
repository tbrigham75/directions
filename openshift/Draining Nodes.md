Managing and draining Nodes
1.	oc adm top nodes
2.	oc get nodes
3.	oc describe node nameofnodetobedrained
4.	oc adm manage-node node2bedrained --schedulable=false  	#Mark it as unschedulable – For Older version of OpenShift 3.11… see #5 for how to do it now
5.	oc adm cordon nameofnode2cordon 	#Mark it as unschedulable
6.	oc adm drain nameofnode2makeunscedulable --delete-emptydir-data --ignore-daemonsets --force - delete empty dir pods, ignore daemonsets
7.	oc adm uncordon <node1>

URLS:
https://docs.openshift.com/container-platform/3.11/admin_guide/manage_nodes.html 
https://docs.openshift.com/container-platform/4.9/cli_reference/openshift_cli/administrator-cli-commands.html#oc-adm-cordon
https://docs.okd.io/4.9/nodes/nodes/nodes-nodes-working.html 


