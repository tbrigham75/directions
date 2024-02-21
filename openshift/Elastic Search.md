When you get an error like this for:  im-app, im-audit, or im-infra:

Job openshift-logging/elasticsearch-im-audit-27830535 failed to complete. Removing failed job after investigation should clear this alert.

Go to:  openshift-logging namespace > Jobs

If a job has ran right afterwards you can delete the failed jobs.  Example:

J
elasticsearch-im-app-27830535
component
=
indexManagement
controller-uid
=
cde5ca64-4738-4b0a-bb78-d3dffce486fd
job-name
=
elasticsearch-im-app-27830535
logging-infra
=
indexManagement
provider
=
openshift
0 of 1	Work queue	

Job
J
elasticsearch-im-app-27831885
component
=
indexManagement
controller-uid
=
557f5651-b9a9-4190-8548-b4fcbe227fbf
job-name
=
elasticsearch-im-app-27831885
logging-infra
=
indexManagement
provider
=
openshift
1 of 1	Work queue	

Job
J
elasticsearch-im-audit-27830535
component
=
indexManagement
controller-uid
=
bd039a42-d4cf-4efd-81bb-0c6229966c09
job-name
=
elasticsearch-im-audit-27830535
logging-infra
=
indexManagement
provider
=
openshift
0 of 1	Work queue	

Job
J
elasticsearch-im-audit-27831885
component
=
indexManagement
controller-uid
=
abd3659f-1713-48e0-a3d4-2573e73e9eb1
job-name
=
elasticsearch-im-audit-27831885
logging-infra
=
indexManagement
provider
=
openshift
1 of 1	Work queue	

Job
J
elasticsearch-im-infra-27830535
component
=
indexManagement
controller-uid
=
8c8e30e5-b57d-4e58-b3f9-c9f741da6813
job-name
=
elasticsearch-im-infra-27830535
logging-infra
=
indexManagement
provider
=
openshift
0 of 1	Work queue	

Job
J
elasticsearch-im-infra-27831885
component
=
indexManagement
controller-uid
=
4d5c190d-cf75-4586-9578-3ec4c6a2c0cb
job-name
=
elasticsearch-im-infra-27831885
logging-infra
=
indexManagement
provider
=
openshift
1 of 1	Work queue