oc get groups | grep chester

Per each group:
oc get projects --as chester --as-group ad-team

For better:
echo "USER:  chester" && oc get projects --as chester --as-group ad-team