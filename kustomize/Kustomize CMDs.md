kustomize build overlays/prod|less - Shows what kustomize file will do

kubectl apply -k overlays/dev  - command to apply the the settings to your cluster

oc apply -k overylays/in-cluster - also works