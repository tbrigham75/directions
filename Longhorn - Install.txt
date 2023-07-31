Partial directions taken from:  https://itnext.io/the-ultimate-guide-to-building-your-personal-k3s-cluster-bf2643f31dd3

1.  kubectl apply -f https://raw.githubusercontent.com/longhorn/longhorn/v1.4.0/deploy/longhorn.yaml

2.  Check everything went smooth
kubectl -n longhorn-system get pod

3.  Check out the longhorn service
kubectl -n longhorn-system get svc

Note below from:  https://forums.rancher.com/t/longhorn-ui-with-traefik/16742
4.  kubectl apply - longhorn-service.yaml
longhorn-service.yaml - Contents:
apiVersion: v1
kind: Service
metadata:
  labels:
    app: longhorn-ui
  name: longhorn-frontend
  namespace: longhorn-system
spec:
  ports:
  - port: 8000
    protocol: TCP
    targetPort: 8000
    name: web
  selector:
    app: longhorn-ui

5.  kubectl apply -f longhorn-ingress.yaml
longhorn-ingress.yaml - Contents:
kind: IngressRoute
apiVersion: traefik.containo.us/v1alpha1
metadata:
  name: longhorn-frontend
  namespace: longhorn-system

spec:
  entryPoints: 
    - web
  routes:
  - match: Host(`192.168.2.101`) 
    kind: Rule
    services:
    - name: longhorn-frontend
      port: 8000