https://www.redhat.com/sysadmin/troubleshooting-terminating-namespaces

More than likely its a finalizer

Per SME - Always make sure you know the root cause before just deleting the finalizer

You can do this a few ways (Not just by what is listed in above link)

1.  Find it in the YAML and delete the finalizer
2.  Export the yaml per the example in website to json and push it
3.  From the Shell:
oc patch deployment/todo-app-deployment -n tomstodo-app --type=json -p'[{"op":"remove","path":"/metadata/finalizers"{]'