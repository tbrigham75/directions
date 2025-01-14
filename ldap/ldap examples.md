KASM:
Name:  Kasm FreeIPA LDAP Settings
Url:  ldaps://servername.home.org:636
Search Base: cn=users,cn=accounts,dc=home,dc=org
Search Filter:  &(objectClass=posixAccount)
Service Acct DN:  uid=svc-kasm,cn=users,cn=accounts,dc=home,dc=org
Group Membership Filter:  (|(cn=*kasm*)(dc=home)(dc=org))

Proxmox
Base Domain Name:  dc=home,dc=org
User Attribute Name:  uid
Bind User:  uid=svc-ldap,cn=users,cn=accounts,dc=home,dc=org
User Filter:  memberOf=cn=proxmox_access,cn=groups,cn=accounts,dc=home,dc=org
Group Filter:  (|(cn=*pve*)(dc=home)(dc=org))