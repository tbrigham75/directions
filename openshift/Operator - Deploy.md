https://docs.openshift.com/container-platform/4.8/operators/admin/olm-adding-operators-to-cluster.html#olm-installing-operator-from-operatorhub-using-cli_olm-adding-operators-to-a-cluster


1. Get subscription (Get the output down to end of Spec)
	oc get sub -o yaml
2. Create Operator Group (Get the output down to end of Spec)
	oc get og -o yaml

In JFROG case these additional things required

3. deploy Postgres
	a. Create Deploy Config
	b. Create Secret (Store in Sealed Secrets)
	c. Create PVC
	d. Create Service

4. Create Master and Join Key
	# Create a key
	export JOIN_KEY=$(openssl rand -hex 32)
	echo ${JOIN_KEY}

5. Modify the Custom Resource (In this case Artifactory HA, An operator might have a custom resource that it defines) to include all required data.  Create .yaml file

5. Create route .yaml file

6. Create Role & Role Binding .yaml file
