Launch an Instance:
1.  EC2
2.  Instances
3.  Launch Instances
4.  Name:  TomsTest01
5.  Select App and OS Images:  Amazon Linux
6.  AMI:  Amazon Linux 2 AMI (HVM)
7.  Instance Type:  t3.micro
8.  Key pair (Either create or select previous created):  toms_key
9.  Network settings > Edit > Subnet > Choose an APP (Example: Dev-mg-dev-us-east-2b-PRIVATE)
10. Network settings > Select existing security group > mgmt-ssh-access
11.  Launch Instance

Tag Instance:
1.  EC2
2.  Instances
3.  Instance ID
4.  Tags > Manage Tags
5.  Add new tag
6.  Name:  ConsumServ:dev:ssh Value: yes	NOTE:  yes must be lowercase
7.  Save

Putty:
1.  You have to convert the pem to ppk with PuttyGen
2.  Get IP from Instance ID
3.  Hostname:  ec2-user@IPADDRESS
4.  

Network:  ProdADSrvAPPPrivateuseast1d


