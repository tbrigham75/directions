For a JSON6902:

1. Edit kustomization.yaml

2. Paste this:
- target:
    version: v1  #Go into file patching and make sure of value
    group: rbac.authorization.k8s.io  #Go into file patching and make sure of value
    kind: ClusterRole  #Go into file patching and make sure of value
    name: admin  #Go into file patching and make sure of value
  path: patch-admin-cr.yaml

3. Create new file:  patch-admin-cr.yaml #From path above

4.  Paste this: (Everything is in JSON in this instance, doesn't neccesarily have to be.  We got this error that let Time know it had to be JSON:
	: yaml: line 4: did not find expected node content)
- op: add
  path: /rules/-	#The dash means add to the end.  If you ever see a 0 (Number) its an array
  value: {
    "verbs": [
      "*"
    ],
    "apiGroups": [
      "apps.gitlab.com"
    ],
    "resources": [
      "runners"
    ]
  }

5. Run this CMD to test:  kustomize build .
