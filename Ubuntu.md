## Linux Ubuntu
#### Network:
Network devices overview:

`ip addr`

### Netplan

Locate the Netplan configuration file:

Typically, these files are located in /etc/netplan/. The filename might be something like 01-netcfg.yaml or 50-cloud-init.yaml.

`sudo nano /etc/netplan/01-netcfg.yaml`

Modify an entry for your network interface 

`
network:
  version: 2
  ethernets:
    enp2s0:
      dhcp4: no
      addresses: [10.255.255.1/24]
      gateway4: <your_gateway_ip>
      nameservers:
        addresses: [<dns_ip_1>, <dns_ip_2>]
`

`
sudo netplan apply
`

### NetworkManager 

Identify the Connection Name: 

`
nmcli con show
`

Assuming your connection name is Wired connection 1 

`nmcli con mod "Wired connection 1" ipv4.addresses 10.255.255.1/24
nmcli con mod "Wired connection 1" ipv4.gateway <your_gateway_ip>
nmcli con mod "Wired connection 1" ipv4.dns "<dns_ip_1>,<dns_ip_2>"
nmcli con mod "Wired connection 1" ipv4.method manual
`

Restart the Network Interface:

`
nmcli con down "Wired connection 1"
nmcli con up "Wired connection 1"
`
