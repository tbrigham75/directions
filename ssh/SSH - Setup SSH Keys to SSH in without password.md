1. Run this CMD to create your keys:
	ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

2. This is only if you create the .ssh folder on your own.  
	mkdir ~/.ssh
	chmod 700 ~/.ssh 	#This is important
	touch ~/.ssh/authorized_keys
	chmod 600 ~/.ssh/authorized_keys 	#This is important

	Copy the below keys to ~/.ssh:
	id_rsa
	id_rsa.pub

	chmod 400 ~/.ssh/id_rsa		#This is important

3. On the remote system
	(If authorized_keys not already there)
	touch ~/.ssh/authorized_keys
	chmod 600 ~/.ssh/authorized_keys 	#This is important
 
4. Edit ~/.ssh/authorized_keys and append the contents of the id_rsa.pub file from system you created keys from