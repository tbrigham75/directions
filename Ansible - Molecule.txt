Molecule - uses Ansible to setup a test envi to run a playbook, do testing, and then tear down env
Intially used to test roles... can now test playbooks

1.  Install:
pip3 install molecule

2. Create a new role with molecule (Notice it creates molecule folder in role):
molecule init role myrole

3.  Test it (test everything and then tear down env):
molecule test

4.  Converge will leave the container running (Can run over again to run changes)
molecule converge

5.  Logon to container:
molecule login
OR:
docker ps 
then: 
docker exec -it into container

Note:  you can throw a fail in playbook and use it like breakpoint

6.  Finished:
molecule destroy

