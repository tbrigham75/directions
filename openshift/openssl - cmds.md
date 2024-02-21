openssl s_client -connect s3.openshift-storage.svc.cluster.local:443 -servername s3.openshift-storage.svc.cluster.local -verify 5 -showcerts

curl -v --cacert ./extra_ca_cert_service-ca.crt https://s3.openshift-storage.svc.cluster.local
 
openssl x509 -in ./service-ca.crt -text
