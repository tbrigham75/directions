1. Edit the vagrant config file:

config.vm.provision "ansible" do [ansible]
	ansible.playbook = "playbook.yml"
end

2. Save it and run (Runs anything in the provision thing above):
vagrant provision