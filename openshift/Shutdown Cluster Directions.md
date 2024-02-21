RH webiste says to do it this way, but if u have alot of nodes it shutdown the masters:

for node in $(oc get nodes -o jsonpath='{.items[*].metadata.name}'); do oc debug node/${node} -- chroot /host shutdown -h 1; done  (DON'T DO IT THIS WAY!)

[2:43 PM] SME
Instead do it this way:
for node in $(oc get nodes -l node-role.kubernetes.io/worker -o jsonpath='{.items[*].metadata.name}'); do oc debug node/${node} -- chroot /host shutdown -h 1; done 

then shutdown the masters.

[2:43 PM] SME
for node in $(oc get nodes -l node-role.kubernetes.io/master -o jsonpath='{.items[*].metadata.name}'); do oc debug node/${node} -- chroot /host shutdown -h 1; done




