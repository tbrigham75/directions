Network tools are not included in most pods.  The below method uses nsenter CMD to kind of enter the container / pod from a Node and still have all CMD's that were available on the Node within the pod after you find out which Node runs the pod.


1.  Logon to Worker Node:
	ssh -i ~/.ssh/id_rsa core@192.168.2.10
2.  Search for program Pod runs:
	sudo crictl ps | grep nginx
3.  Verify through the web console that a portion of the ID cri-o://74910 is the same as the container ID from above output:
	Pods > Select pod you are searching for > Scroll down to Containers and select the Container > Look for something similiar:  ID cri-o://74910
	NOTE:  If Pod is rebuilding the # might change
4.  Inspect container (Get number from step 2:
	sudo crictl inspect 74910bb689894 | less
5.  Search for the pid:
	"pid": 4004167 
6.  Get running process from Node:
	ps aux | grep 4004167
7.  Open Terminal to the pod and pull ID:
	sh-4.4$ id
	uid=1000720104
8.  Halfway enter into the container, but keeps local CMD's to the node:
	sudo nsenter -t 4004167 -n /bin/bash
9.  Get IP info:
	ip a s
10.  Verify in Web Console:
	Pods > Podname > Details > Look for Pod IP
11.  Do a netstat for ports:
	netstat --tcp -a --listen
	or:
	netstat --tcp -a --listen -n
12.  Can verify found ports and ensure the Service's match up from Web Console
	Networking > Services
13.  You can also do curl CMD's just remember you are in a container / Pod so use localhost:
	curl http://localhost:8080/
14.  Can also grep for ports from the services:
	netstat --tcp -a --listen -n | grep 30488
