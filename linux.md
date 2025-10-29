## Linux Ubuntu

## 1 System :

### Navigation
Print current directory path:
`pwd`</br>
Current directory:
`./`</br>
Root directory:
`/`</br>
home directory:
`cd ~`</br>
previous directory:
`cd -`</br>
List with details (permissions, size, date):
`ls -l`</br>
List with human-readable sizes:
`ls -lh`</br>
Show hidden files (starting with .):
`ls -a`</br>
List by time, newest last:
`ls -ltr`</br>
List by size, largest first:
`ls -lS`</br>
### Listing, Filtering
List only .txt files:
`ls *.txt`</br>
List files containing "read":
`ls *read*`</br>
Filter list output:
`ls | grep "pattern"`</br>
Show only Python files:
`ls -l | grep ".py$"`</br>
Show directory tree structure:
`tree`</br>
Limit tree depth to 2 levels:
`tree -L 2`</br>
### File View
Display entire file:
`cat file.txt`</br>
View file page-by-page (q to quit):
`less file.txt`</br>
Show first 10 lines:
`head file.txt`</br>
Show first 20 lines:
`head -n 20 file.txt`</br>
Show last 10 lines:
`tail file.txt`</br>
Follow file in real-time (logs):
`tail -f logfile.log`</br>
### Directory Management
Create nested directories:
`mkdir -p path/to/dir`</br>
Remove empty directory:
`rmdir dirname`</br>
Delete file:
`rm file.txt`</br>
Delete directory and contents:
`rm -r dirname`</br>
Force delete (use carefully!):
`rm -rf dirname`</br>
Copy file:
`cp file dest`</br>
Copy directory recursively:
`cp -r dir1 dir2`</br>
Rename/move file:
`mv oldname newname`</br>
Create empty file or update timestamp:
`touch file.txt`</br>
### Search
Find all .c files from current dir:
`find . -name "*.c"`</br>
Find files/folders with 'read' anywhere in the name, case insensitive:
`find . -name "*.c"`</br>
Find Only directories containing 'log':
`find ./ -type d -iname "*log*" `</br>
Find files starting with "read":
`find /path -type f -name "read*"`</br>
Find directories starting with "lib":
`find /path -type d -name "lib*"`</br>
Search for text in file:
`grep "text" file.txt`</br>
Search recursively in directory:
`grep -r "pattern" /path`</br>
Case-insensitive search:
`grep -i "pattern" file`</br>
Show path to command executable:
`which command`</br>
### File Info
Show file type:
`file filename`</br>
Show detailed file information:
`stat filename`</br>
Show directory size:
`du -sh dirname`</br>
Show absolute path of file:
`readlink -f file`</br>


## 2) Commands
When bash sees \ at the end of a line, it treats the next line as part of the same command:
`\`

## 3) Network
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

## 3 Auto Start:

`sudo chmod +x /home/linux/select_app/selector.py
`

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

## 4 Others
Unrequire password with "sudo" commands:</br>
`
sudo visudo
`</br>
`
linux ALL=(ALL) NOPASSWD: /bin/systemctl start home.service, /bin/systemctl stop home.service
`</br>

change keyboard layout:</br>
`
setxkbmap cz
`</br>
