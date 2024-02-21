$ docker login --username "$(oc whoami)" --password-stdin https://default-route-openshift-image-registry.apps.dev.org < <(oc whoami -t)

Can change the trusted-images below to the namespace to push image stream to namespace:

$ docker tag tbrigham/catnip:latest default-route-openshift-image-registry.apps.dev.org/trusted-images/catnip:v1.0

Other example:
docker tag tbrigham/gitea_rootless:latest quay.apps.dev.org/tbrigham/public/gitea_rootless:v1.17.3

$ docker push default-route-openshift-image-registry.apps.dev.org/trusted-images/catnip:v1.0

Other example:
docker push quay.apps.dev.org/tbrigham/public/gitea_rootless:v1.17.3

quay.apps.dev.org/tbrigham/public/ubi-gitea:latest


