bases:
- ../../base

resources:
- cr-gitlab-runner-sa-annotate.yaml
- crb-argocd-manager.yaml
- grp-devops.yaml
- rb-gitlab-runner-sa-annotate.yaml
  
patchesJson6902:
- target:
    version: v1
    group: rbac.authorization.k8s.io
    kind: RoleBinding
    name: admin
  path: patch-portal-admin-binding.yaml
- target:
    version: v1
    group: rbac.authorization.k8s.io
    kind: ClusterRoleBinding
    name: portal-management
  path: patch-portal-svcacct-binding.yaml
- target:
    version: v1
    group: user.openshift.io
    kind: Group
    name: ti-build-editors
  patch: |-
    - op: add
      path: /users/-
      value: username1
      value: username2
- target:
    version: v1
    group: user.openshift.io
    kind: Group
    name: trusted-images-editors
  patch: |-
    - op: add
      path: /users/-
      value: username    
- target:
    version: v1
    group: rbac.authorization.k8s.io
    kind: ClusterRole
    name: admin
  path: patch-admin-cr.yaml
  