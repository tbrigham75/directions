1. wget https://cloud-images.ubuntu.com/minimal/releases/jammy/release/ubuntu-22.04-minimal-cloudimg-amd64.img

2.  Rename image - important change extension:
mv ubuntu-22.04-minimal-cloudimg-amd64.img ubuntu-22.04-min-15gb.qcow2

3. Resize the image:
qemu-img resize ubuntu-22.04-min-15gb.qcow2 15G

4. Go to Web Gui > Create VM > VM ID: 900 > Name: ubuntu-22.04-min-8gb > Start at boot checked > OS: Don't use any media >
Qemu Agent checked > Disks click trash can > Next to Confim and Finish

4. Import image into ProxMox:
sudo qm importdisk 900 ubuntu-22.04-min-8gb.qcow2 local-zfs

5. Set vga console or u won't see anything on screen when it boots (900 is VM ID):
sudo qm set 900 --serial0 socket --vga serial0

6.  Go to Web Gui > Hardware > Add > CloudInit Drive > Select Storage 

7.  Hardware > Notice Unused Disk > Edit > Add

8.  CloudInit > Add: User, Password, DNS Servers, SSH public key, IP Config

9.  Option > Boot Order > Put a Check in Hard Drive box > Drag to boot Position > Uncheck Net0

10. Option > Start at Boot > Check

11. Check that it boots and install any software you want before turning into a Template

12. Right click VM > Convert to Template !!! BE SURE everything set no way to revert back.

13.  You might want to clone it and turn the clone to a template

