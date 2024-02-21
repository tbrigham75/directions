MSGs from Mentor:
The argo application resource supports an ignore Differences element. You can add a resource type and path and Argo will not overwrite that path if the value is different from the repo. The JFrog one already has one. Add the path to replicas to the jsonPointers array of the DeploymentConfig entry.

No. Add the /spec/replica to the jsonPointers list for the DeploymentConfigentry that already exists in the ApplicationSet template for JFrog.

----------------------------------------------
This is so it will not auto deploy replicas:

apiVersion: argoproj.io/v1alpha1
kind: ApplicationSet
metadata:
  name: jfrog-operator
  namespace: openshift-gitops
spec:
  generators:
    - list:
        elements:
          - cluster: dev
            url: https://api.labdev.org:443
          - cluster: prod
            url: https://api.lab.org:6443
  syncPolicy:
    preserveResourcesOnDeletion: true
  template:
    metadata:
      name: jfrog-{{cluster}}
      namespace: openshift-gitops
    spec:
      destination:
        namespace: jfrog
        server: '{{url}}'
      ignoreDifferences:
        - group: apps.openshift.io
          kind: DeploymentConfig
          jsonPointers:
            - /spec/template/spec/containers/0/image
	######You add the stuff here:########
            - /spec/replica
      project: proj-infra
      source:
        path: jfrog-operator/overlays/{{cluster}}
        repoURL: 'https://gitlab.org/devops/third-party-operators.git'
        targetRevision: HEAD
      syncPolicy:
        automated:
          selfHeal: true
        syncOptions:
          - CreateNamespace=false
          - ApplyOutOfSyncOnly=true
          - RespectIgnoreDifferences=true
