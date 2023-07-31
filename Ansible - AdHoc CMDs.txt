1.  Ping servers
ansible linux -m ping -u username

2.  Free space
ansible servers -a "free h" -u username

3.  Get hostname
ansible servers -a "hostname"

4. Gather facts:
ansible - inventory servers -m setup

5.  Become root and yum installs ntp
ansible -i inventory servers -b -m yum -a "name=ntp state=present"

6.  Get info from CMD for CMD:
ansible-doc service

7.  Update GIT repo on remote server:
ansible -i inventory servers -b -m git -a "repo=github_url_goes_here dest=/opt/ app update=yes version=1.2.4"

8.  Ansible list out your inventory:
ansible-inventory --list -i inventory
