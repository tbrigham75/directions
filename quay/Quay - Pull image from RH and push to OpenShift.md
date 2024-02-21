https://developers.redhat.com/blog/2020/03/24/red-hat-universal-base-images-for-docker-users#red_hat_enterprise_linux_and_docker

1.	OC logon first
2.	Logon to repo with docker:  
docker login --username "$(oc whoami)" --password-stdin default-route-openshift-image-registry.apps.dev.org < <(oc whoami -t)
If that fails try without https:// or try with podman:
podman login --username "$(oc whoami)" --password-stdin default-route-openshift-image-registry.apps.dev.org < <(oc whoami -t)
3.	Another way to try and logon directly to Quay:
docker login --username tbrigham https://quay.apps.dev.org
4.	Build image from Dockerfile:
docker image build -t tomtest .
5.	Get docker images:
docker image list
6.	Tag the image:
docker tag tomtest default-route-openshift-image-registry.appsdev.org/trusted-images/tomtest:v1.0
7.	Push the image:
docker push default-route-openshift-image-registry.apps.dev.org/trusted-images/tomtest:v1.0
8.	To delete Repo’s look in Quay Web Console > Click Repo > Look for Gear > Delete Repo
