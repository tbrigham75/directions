Example used is proj-portal:

1.  Search portal in Web Console

2.  Select the portal pod (Only pod without something else on it).  This example:  portal-40-gkgf9

3. After clicking Pod look for:  
Node
test-p9c9z-worker-n5wjp

4.  Gets into pod running on that node (Creates in your active project so pay attention to where you run):
#Creates:  test-p9c9z-worker-n5wjp-debug pod.
oc debug node/test-p9c9z-worker-n5wjp

5.  Find pod in Web Console and look at Volumes half way down page and it shows it mounts a /host folder.  This is a mount to the host file system of the pod.

6.  Do ls and notice the /host folder

7.  When you first logon this shows in Shell - To use host binaries, run `chroot /host`:
chroot /host

8.  After the chroot notice a ls doesn't show the /host

9.  Show all containers running on the host:
crictl ps

10.  crictl ps | grep portal

11.  crictl inspect df8c07d04facc | less

12.  Look for PID:  
crictl inspect df8c07d04facc | less
or
crictl inspect df8c07d04facc | grep "pid"

13.  Aux the ID and find process that is running the portal application
ps aux | grep 3977043

Results:
1001410+ 3977043  0.0  0.0  11928  3032 ?        Ss   Oct11   0:00 /bin/bash /tmp/scripts/run

3977043 = Process ID
14.  Verify its container running portal:  Go back to webconsole and select portal pod.  You'll notice it has 1 conatiner in it, if you click the container further down on pod page you'll see it has the the ID that matches df8c07d04facc in longer format:  cri-o://df8c07d04facc53c06ea7a5c500ee32ce702f8c7934502461d465af0dbb9f0fb

15. Show all IP's for all interfaces on host:
ip a sh

Results - shows alot!

16.  Now you know process ID - 3977043.  The following CMD enters a namespace associated with that process:
nsenter -t 3977043 -n /bin/bash

17.  Notice prompt changes, running a Shell that still has access to anything running on the host, but if you do something like network action it only shows interfaces that container can see.  Do same IP address show CMD as above to see:
ip a sh

18.  Get IP from above CMD and go to container in webconsole and you'll see it matches the IP

19.  Type exit a bunch of times to get out of everything.

NOTE:  oc debug changes the entry point and bypasses script that was supposed to run... it will run program you tell it to... typically /bin/bash

