## Lab Report: Host Based Network Defense with Ubuntu Firewalls ## 
**Student Name:** Ean Dudley 

**Course:** Cyber 262 Cyber Defense Studio

**Instructor:** Professor Joe Royer

**Date:** 08/24/2022 

## Add User to Ubuntu Machine ##
```bash
useradd -m -p "$(openssl passwd -6 $PASS)" $USER
```

**Deliverable 1.1: Screenshot Showing the Victim Ubuntu Machine /etc/passwd file with the new user ebd5287 added**
![image](https://github.com/Ean-Dudley-Portfolio/Cybersecurity-Portfolio/assets/57103612/c42ce8e3-f42a-40b4-81d9-b5df02554efe)


## User Zenmap to scan the Victim Machine (192.168.0.1/24) ##

![image](https://github.com/Ean-Dudley-Portfolio/Cybersecurity-Portfolio/assets/57103612/76de98ee-7c12-429d-a828-7feb6a7f9a8c)

*** Running Services / Open Ports ***
| Port | Service | 
|------|---------|
| 21   | FTP     |
| 22   | SSH     |
| 23   | Telent  |
| 80   | HTTP    |


## Use Ncrack against the Victim Machine to crack the password for new user ## 
```bash
ncrack -v -p 23 -u ebd5287 default.pwd 192.168.0.1
```
This command runs a password crack for the user ebd5287 on port 23 (Telent) using thee default password list (default.pwd). The -v option means that this program runs in verbose mode. 

![image](https://github.com/Ean-Dudley-Portfolio/Cybersecurity-Portfolio/assets/57103612/2f0a2997-e8f1-433f-8536-45d0d49b66e1)


ncrack successfully cracked the password for user ebd5287 with the pasword 1234567

## Install, Enable, and Configure UFW ##
``` bash
#Install UFW
sudo apt-get install ufw

#Enable UFW
ufw enable

#Per Instructions, set default deny on incoming traffic
ufw default deny incoming

#Allow FTP incoming on port 21 over TCP from 192.168.0.4


#Allow SSH incoming on port 22 over TCP from 192.168.0.4
```
