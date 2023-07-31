Directions from bottom of page:  https://forums.rancher.com/t/k3s-traefik-dashboard-activation/17142/16

Being Traefik is an ingress router, all I did was create an Ingress rule to access the Dashboard in name space “kube-system”. I used entrypoint websecure since I already have LetsEncrypt working, you can change to just web.

$ cat traefik_ingress.yaml 
---
apiVersion: traefik.containo.us/v1alpha1
kind: IngressRoute
metadata:
  name: dashboard-ingressroute
  namespace: kube-system
spec:
  entryPoints:
    - web
  routes:
    - match: Host(`192.168.2.101`) && (PathPrefix(`/dashboard`) || PathPrefix(`/api`))
      kind: Rule
      services:
        - name: api@internal
          kind: TraefikService

Apply the yaml file:

$ kubectl apply -f traefik_ingress.yaml 
ingressroute.traefik.containo.us/dashboard-ingressroute created

And then point my web browser to https://mydomain/dashboard and the dashboard comes right up.