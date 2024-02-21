Digging deeper into OpenShift postgres Web GUI example:

1.  Select OpenShift Project in Web GUI
2.  Builds > ImageStreams > Postgressql
3.  Scroll down under Details tab, select latest in this case:  postgresql:13-el8
4.  Scroll down in Details tab
5.  Look for Env Vars:
	STI_SCRIPTS_PATH	/usr/libexec/s2i
	CONTAINER_SCRIPTS_PATH	/usr/share/container-scripts/postgresql
6.  Workloads > Pods > search for postgresql
7.  Project ti-build has one

Digging deeper into OpenShift postgres CLI example:

1.  oc project openshift
2.  oc get istag | grep postgres
3.  Get the SHA
4.  Image stream is like a Docker inspect.  Add @SHA to end of:
	oc get isimage postgresql@sha256:32f1d6b012ed6c5163a390ba7ff66e01894004674b727744760ffb68bb044d74 -o 		yaml | less
5.  Look for this:
  Config:
      Cmd:
      - run-postgresql
      Entrypoint:
      - container-entrypoint
6.  You can also find the path:
	STI_SCRIPTS_PATH=/usr/libexec/s2i
	CONTAINER_SCRIPTS_PATH=/usr/share/container-scripts/postgresql

Digging deeper inside container:
1.  Open a terminal in a postgresql pod (#6 in Digging deeper into OpenShift postgres Web GUI example:)
2.  which container-entrypoint
3.  cat /usr/bin/container-entrypoint
	#!/bin/bash
	exec "$@" #NOTE:  Execs all Arguments
4.  which run-postgresql
5.  cat /usr/bin/run-postgresql | more
6.  Notice:  
	check_env_vars
	generate_passwd_file
7.  Is a function in the file for:  generate_passwd_file?  No then look for source:
	source "${CONTAINER_SCRIPTS_PATH}/common.sh" #NOTE:  there could also be a . (dot sourced file)
8.  which common.sh
	Comes back with no common.sh in (bunch of paths).  Its not in the system path so it can't find it.
9. Have BASH tell you the ENV Var:  
	echo $CONTAINER_SCRIPTS_PATH
	/usr/share/container-scripts/postgresql
10.  cd /usr/share/container-scripts/postgresql
11.  Look for the function:
	cat common.sh |more

# Generate passwd file based on current uid
function generate_passwd_file() {
  export USER_ID=$(id -u)
  export GROUP_ID=$(id -g)
  grep -v -e ^postgres -e ^$USER_ID /etc/passwd > "$HOME/passwd"
  echo "postgres:x:${USER_ID}:${GROUP_ID}:PostgreSQL Server:${HOME}:/bin/bash" >> "$HOME/passwd"
  export LD_PRELOAD=libnss_wrapper.so
  export NSS_WRAPPER_PASSWD=${HOME}/passwd
  export NSS_WRAPPER_GROUP=/etc/group
}

Find running IDs of Postgres:
1.  ps aux | grep postgres
1000610+       1  0.0  0.0 297480 23696 ?        Ss   Jan17   1:13 postgres
1000610+      61  0.0  0.0 149720  5604 ?        Ss   Jan17   0:00 postgres: logger   
1000610+      63  0.0  0.0 297608  6528 ?        Ss   Jan17   0:00 postgres: checkpointer   
1000610+      64  0.0  0.0 297624  5940 ?        Ss   Jan17   0:06 postgres: background writer   
1000610+      65  0.0  0.0 297480 10044 ?        Ss   Jan17   0:06 postgres: walwriter   
1000610+      66  0.0  0.0 298172  8872 ?        Ss   Jan17   0:11 postgres: autovacuum launcher   
1000610+      67  0.0  0.0 151984  5888 ?        Ss   Jan17   0:26 postgres: stats collector   
1000610+      68  0.0  0.0 298044  7040 ?        Ss   Jan17   0:00 postgres: logical replication launcher   
1000610+ 2279108  0.0  0.0   9116   912 pts/2    S+   18:38   0:00 grep postgres
2.  sh-4.2$ id
uid=1000610000(1000610000) gid=0(root) groups=0(root),1000610000
3.  Notice the UID and compare to above ps aux
4.  Not the same ID
	grep postgres /etc/passwd
	postgres:x:26:26:PostgreSQL Server:/var/lib/pgsql:/bin/bash



Using the LDD CMD to find .SO files (Shared Libraries - Like DLL files)
1. which postgres
	/opt/rh/rh-postgresql12/root/usr/bin/postgres
2.  CMD shows the shared libraries in use by program:
	ldd /opt/rh/rh-postgresql12/root/usr/bin/postgres

	
