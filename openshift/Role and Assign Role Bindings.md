oc create role jfrog-nginx --verb=use --resource=scc --resource-name=anyuid -n jfrog

oc adm policy add-role-to-user jfrog-nginx default --role-namespace=jfrog -n jfrog