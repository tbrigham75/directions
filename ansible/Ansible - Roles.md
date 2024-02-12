1.  Setup Ansible Galaxy role structure:
ansible-galaxy role init NameOfRole

2.  Install Ansible Galaxy Role:
ansible-galaxy role install RoleNameOnGalaxy

3.  The default role search path is ~/.ansible/roles:/usr/share/ansible/roles:/etc/ansible/roles

4.  You can also config the Ansible.cfg file for path to roles:
roles_path = ~/.role
