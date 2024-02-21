oc get templates -n openshift | grep postgres

oc process -n openshift postgresql-persistent --parameters

oc new-app --name=postgresql --template=postgresql-persistent -p POSTGRESQL_DATABASE=artifactory

