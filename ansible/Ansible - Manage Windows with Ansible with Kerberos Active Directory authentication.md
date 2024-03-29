https://www.youtube.com/watch?v=M18yDGAd9TU&t=1186s

https://www.virtualizationhowto.com/2018/04/configure-ansible-windows-server-kerberos-authentication-in-ubuntu/

1.  Install Ansible along with other dependencies:
sudo apt-get install gcc python-dev libkrb5-dev -y

sudo apt upgrade

sudo apt-get install python3-pip -y

pip3 install --upgrade pip

pip3 install --upgrade virtualenv

pip3 install pywinrm

sudo apt install krb5-user -y

sudo apt-get install python3-kerberos -y

pip3 install ansible

NOTE:  Had to add this:

pip install --upgrade pip setuptools wheel

sudo apt install libcairo2 libcairo2-dev pkg-config python3-dev

pip3 install pycairo

sudo apt-get install gcc python2-dev libkrb5-dev

pip3 install pywinrm[kerberos]

2.  Edit:  /etc/krb5.conf with, modify to your domain info (Notice CAPS for Domain info):

[logging]
 default = FILE:/var/log/krb5libs.log
 kdc = FILE:/var/log/krb5kdc.log
 admin_server = FILE:/var/log/kadmind.log

[libdefaults]
 default_realm = MYDOMAIN.LOCAL
 allow_weak_crypto = true
 dns_lookup_realm = false
 dns_lookup_kdc = false
 rdns = false
 ticket_lifetime = 24h
 renew_lifetime = 7d
 forwardable = true

[realms]
 MYDOMAIN.LOCAL = {
  kdc = dc1.mydomain.local
  admin_server = dc1.mydomain.local
 }

3.  kinit admin@CLOUD.LOCAL
klist – list Kerberos tickets
kdestroy -A – Removes existing Kerberos tickets

4. Create group_vars/windows.yml, ansible.cfg, and inventory.ini:
	
group_vars/windows.yml
ansible_user: Admin@HOME.ORG
ansible_connection: winrm
ansible_port: 5985
ansible_winrm_transport: kerberos
#ansible_winrm_cert_validation: ignore

ansible.cfg
[defaults]
inventory = inventory/inventory.ini

inventory.ini
[windows]
2022winsrv01.HOME.ORG

5.  Create main.yml for a task:

---
name: "Chocolatey"
hosts: windows
tasks:
  - name: Install Google Chrome
  win_chocolatey:
    name: googlechrome
    state: present
    ignore_checksums: yes

6.  Test connection to windows servers:
ansible windows -i inventory/inventory.ini -m win_ping -v

https://www.devopsschool.com/tutorial/ansible/ansible-windows-remote-setup.html

7.  Run this script within PowerShell ISE:
$url = "https://raw.githubusercontent.com/jborean93/ansible-windows/master/scripts/Upgrade-PowerShell.ps1"
$file = "$env:temp\Upgrade-PowerShell.ps1"
$username = "Administrator"
$password = "P@ssw0rd"

(New-Object -TypeName System.Net.WebClient).DownloadFile($url, $file)
Set-ExecutionPolicy -ExecutionPolicy Unrestricted -Force

# version can be 3.0, 4.0 or 5.1
&$file -Version 5.1 -Username $username -Password $password -Verbose

$reg_winlogon_path = "HKLM:\Software\Microsoft\Windows NT\CurrentVersion\Winlogon"
Set-ItemProperty -Path $reg_winlogon_path -Name AutoAdminLogon -Value 0
Remove-ItemProperty -Path $reg_winlogon_path -Name DefaultUserName -ErrorAction SilentlyContinue
Remove-ItemProperty -Path $reg_winlogon_path -Name DefaultPassword -ErrorAction SilentlyContinue

$url = "https://raw.githubusercontent.com/ansible/ansible/devel/examples/scripts/ConfigureRemotingForAnsible.ps1"
$file = "$env:temp\ConfigureRemotingForAnsible.ps1"

(New-Object -TypeName System.Net.WebClient).DownloadFile($url, $file)

powershell.exe -ExecutionPolicy ByPass -File $file

8.  How to setup GPO for WinRM:
https://support.auvik.com/hc/en-us/articles/204424994-How-to-enable-WinRM-with-domain-controller-Group-Policy-for-WMI-monitoring




