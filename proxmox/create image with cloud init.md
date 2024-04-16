https://www.youtube.com/watch?v=Kv6-_--y5CM

CLI:
1. Goto:  https://cloud-images.ubuntu.com/
2. Browse into distro name and current
3. Best image to pick is -kvm.img   --Kernel VM
4. You can manually download or go to ProxMox and click the ISO location and download with URL
5. Go to the ProxMox shell to create new VM:
	qm create 5000 --memory 2048 --core 2 --name ubuntu-cloud-temp --net0 virtio,bridge=vmbr0
6. Change to your ISO location:
	cd /var/lib/vz/template/iso/
7. Import .img into VM: 
	qm importdisk 5000 lunar-server-cloudimg-amd64-disk-kvm.img LinuxVMs
	#NOTE:  5000 = ID of VM and LinuxVMs = name of storage
8. Attach Hard Drive to VM:
	qm set 5000 --scsihw virtio-scsi-pci --scsi0 LinuxVMs:vm-5000-disk-0
9. Setup cloudinit as a cdrom:
	qm set 5000 --ide2 LinuxVMs:cloudinit
10. Set cloudinit as boot drive:
	qm set 5000 --boot c --bootdisk scsi0
11. Equivalent of pluggin in a VGA monitor (Allows opening proxmox console to VM):
	qm set 5000 --serial0 socket --vga serial0
	
WebGUI:
1. Highlight 5000 VM and go to hardware
2. Go into Processors:
	a. Check Enable NUMA
	b. Type > Change to Host  #Uses host processor instead of virtual setup.
3. Go into Hard Disk:
	a. Click SSD emulation	#you can reclaim unused space if using SSDs or nvme
4. Setup Cloud Init:
	a. Highlight VM
	b. Click Cloud-Init
	c. Edit each:  User, Password, you can do SSH public keys also 
5. Right Click VM and select Convert to template