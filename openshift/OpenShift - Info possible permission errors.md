Openshift runs images as arbitrary user.

Most all error in OpenShift will be permission errors, but may not be obvious:

Example:  Failed to read config /var/lib/neo4j/conf/neo4j.conf: Unrecognized setting. No declared setting with name: SERVICE.SERVICE.HOST. Cleanup the config or disable 'server.config.strict_validation.enabled' to continue.
Run with '--verbose' for a more detailed error message.

Has a lot of tips:
https://docs.openshift.com/container-platform/4.9/openshift_images/create-images.html#images-create-guide-general_create-images