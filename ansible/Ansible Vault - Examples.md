1.  Encyrpt:
ansible-vault encrypt vars/api-key.yml

2.  Ask Password when running playbook
ansible-playbook mail.yml --ask-vauly-pass

3.  Use a password file instead of using vault... make sure you ignore files if they are going to GIT
ansible-playbook mail.yml --vault-password-file ~/.ansible/api-key.yml

4.  If you need to decrypt, but its better to do #5 and edit
ansible-vault decrypt vars/api-key.yml

5.  Edit vault key:
ansible-vault edit /vars/api-key.yml

6.  Rekey the password:
ansible-vault rekey vars/api-key.yml
