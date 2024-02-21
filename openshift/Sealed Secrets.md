2 Ways to do:

#1 - Converting a secret yaml to a sealed

1.  If starting with a yaml file , convert secret to json file:
yq r -j postgres-secret.yaml > postgres-secret.json

2.  kubeseal --controller-namespace sealed-secrets --controller-name sealedsecretcontroller-sealed-secrets < secret_to_seal.json > sealed_secret.json

Example:  kubeseal --controller-namespace sealed-secrets --controller-name sealedsecretcontroller-sealed-secrets < gitearobot-pull-secret.json > gitearobot-se
aled-secret.json

(Note:  In a Secret, the values of all data elements are supposed to be Base64 encoded strings.  So the above will not work if the YAML doesn't contain those values in Base64.  Follow #2 below for a better way to create this in the shell)

#2 - Creates json file with literals inputed during CMD:

1.  Creates desired JSON file:
oc create secret generic db-secret -n tom-gitea -o json --dry-run=client --from-literal=database-user=gitea --from-literal=database-password=passwordgoeshere > gitea-sealed-secret.json

(Note from SME:  Or use the oc command like I did above.  I specified --dry-run=client so nothing actually get created on the server, and -j json to generate output in JSON that could be sent directly to kubeseal if you wanted.  Then the data elements can be specified using one or more --from-env-file, --from-file, or --from-literal arguments.)

#  Additional Things you can do:

1. If you want to convert json back to yaml:
yq r sealed_secret.json

2.  If you have the normal secret in git you can add it to a .gitignore file to not auto upload to git.  This file can be any where in your git repo... I'm going to start placing it in same folder as file.


Questions I asked about finding something online:

Why didn't work:

kubeseal --fetch-cert --controller-namespace="sealed-secrets" --controller-name="sealedsecretcontroller"
kubeseal --controller-namespace sealed-secrets --controller-name sealedsecretcontroller-sealed-secrets <test.json> sealed_secret.json

It had the wrong controller name... best practice to let OpenShift do its thing controlling the certs and use correct CMD in #2 above.


by default it will not override secret:
Message
SyncedFalse
1 minute ago
-failed update: Resource "db-secret" already exists and is not managed by SealedSecret

