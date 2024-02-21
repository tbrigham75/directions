1. First you have to create an operator through:
third-party-operators

2. Then you create either an Application or Application Set (Most used) in: dev-bootstrap.
	Under Spec you need this for the clusters you will manage:
spec:
  generators:
    - list:
        elements:
          - cluster: dev
            url: https://api.dev.org:443
          - cluster: in-cluster
            url: https://kubernetes.default.svc
          - cluster: prod
            url: https://api.lab.org:6443

3. Modify: appproj-infra.yaml per each Operator and try to keep it alphabetized

	Server can be either of the 3 clusters:
	'https://kubernetes.default.svc'
	'https://api.lab.org:6443'
	Most of time it is '*' for all 3.


