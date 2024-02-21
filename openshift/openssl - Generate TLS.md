openssl req -x509 -nodes -days 365 -newkey rsa:2048 -out ingress-tls.crt -keyout ingress-tls.key -subj "/CN=hostname.example.com/O=hostname"


Example:
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -out tls.crt -keyout tls.key -subj "/CN=artifactory.dev.org/O=artifactory"

oc create secret tls my-tls-secret --namespace jfrog --cert tls.crt --key tls.key
