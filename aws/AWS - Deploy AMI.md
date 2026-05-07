1. AMI > Select AMI > Launch instance from AMI > Choose the sysprepped image

2.  Provide:  Name, Instance Type, and Key Pair

3.  Edit Network settings and pick same network other instances are on.

4.  Select existing security groups and pick same ones other instances are on.

5.  Everything else are defaults.  Click Launch instance

6.  Watch:  Status check to change from Initializing to 3/3 checks passed

7.  Set required Tags, compare to other instances tags

7.  Click Instance ID > Connect > RDP Client > Get Password > Upload private key file > Decrypt password > Copy IP and Password > Connect with RDP

8.  Run updates

9.  Rename PC and reboot

10.  Change DNS to 2 DC IPs > Add to Domain with fully qualified DNS name

11.  Reboot and logon with a Domain Acct

12.  Install any additional software required and setup any additional customizations