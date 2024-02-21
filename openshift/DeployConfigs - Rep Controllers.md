Rep Controllers are like a copy of Deploy Config.

I was troubleshooting an issue where I had to delete a PVC... but couldn't cause things were tied to it.

I had to turn off replicas in the as-jfrog.yaml by doing adding this  - /spec/replicas:
      ignoreDifferences:
        - group: apps.openshift.io
          kind: DeploymentConfig
          jsonPointers:
            - /spec/template/spec/containers/0/image
            - /spec/replicas

I should have then deleted the replication controllers and then I could have deleted the PVC.