Checks certs that a website uses:

openssl s_client -connect oauth-openshift.apps.org:443 -servername oauth-openshift.apps.org -verify 5 -showcerts