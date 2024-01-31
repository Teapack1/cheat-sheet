## Linux Ubuntu
## 1  Network:
Network devices overview:

`ip addr`

### Netplan

Locate the Netplan configuration file:

Typically, these files are located in /etc/netplan/. The filename might be something like 01-netcfg.yaml or 50-cloud-init.yaml.

`sudo nano /etc/netplan/01-netcfg.yaml`

Modify an entry for your network interface 

```
network:
  version: 2
  ethernets:
    enp2s0:
      dhcp4: no
      addresses: [10.255.255.1/24]
      gateway4: <your_gateway_ip>
      nameservers:
        addresses: [<dns_ip_1>, <dns_ip_2>]
```

`
sudo netplan apply
`

### NetworkManager 

Identify the Connection Name: 

`
nmcli con show
`
See the ports specifications:
`
nmcli device show enp2s0
`</br>
`
nmcli device show enp1s0
`</br>


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

## 2  Auto Start:

`sudo nano /etc/systemd/system/yourscript.service
`

```
[Unit]
Description=Mediapipe
After=network.target

[Service]
ExecStart=/usr/bin/python3 /home/linux/hand-gesture-control-mediapipe-artnet/app.py
WorkingDirectory=/home/linux/hand-gesture-control-mediapipe-artnet
StandardOutput=inherit
StandardError=inherit
Restart=always
User=linux

[Install]
WantedBy=multi-user.target

[Service]
Environment="DISPLAY=:0"
```

`sudo systemctl daemon-reload`

`
sudo systemctl enable yourscript.service
`

`
sudo systemctl disable yourscript.service
`


`
sudo systemctl start yourscript.service
`

`
sudo systemctl status yourscript.service
`

`
journalctl -u yourscript.service
`

<b>Review services:</b></br>
`
systemctl list-unit-files --type=service --state=enabled
`</br>
`
systemctl list-units --type=service --state=running
`</br>

### Others
Unrequire password with "sudo" commands:</br>
`
sudo visudo
`</br>
`
linux ALL=(ALL) NOPASSWD: /bin/systemctl start home.service, /bin/systemctl stop home.service
`</br>
