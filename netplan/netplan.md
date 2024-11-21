1.  Edit the file in and put below yaml in file:  /etc/netplan/01-netcfg.yaml
    network:
    version: 2
    renderer: networkd
    ethernets:
        ens18:
        dhcp4: no
        addresses: [192.168.1.11/24]
        routes:
            - to: default
            via: 192.168.1.1
        nameservers:
            addresses: [192.168.1.53]
2.  Run this:
    sudo netplan apply


