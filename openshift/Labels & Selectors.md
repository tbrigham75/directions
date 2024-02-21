kind: Deployment
apiVersion: apps/v1
metadata:
  name: gitea-db
  namespace: tom-gitea
  labels:
    app: gitea #sets labels for deployments u can search (Does not need to match below 2)
spec:
  replicas: 1
  selector:
    matchLabels:
      app: gitea #Finds pod assoc with this deployment - determines search filter to this deployment (Selector label and template label will be same)
  template:
    metadata:
      labels:
        app: gitea #When new replica builds it assigns label to pod (Selector label and template label will be same)

Note:  If you have 2 separate deployments they should NOT have the same name for the labels
  