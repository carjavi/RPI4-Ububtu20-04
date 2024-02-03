<p align="center"><img src="./img/raspubun.webp" height="200" alt=" " /></p>
<h1 align="center">Raspberry Pi 4 with Ubuntu 20.04 LTS 64-bit ARM Server</h1> 
<h4 align="right">February 24</h4>

<br>

<img src="https://img.shields.io/badge/OS-Linux%20GNU-yellowgreen">
<img src="https://img.shields.io/badge/Hardware-Raspberry%20ver%204-red">

<br>

# How to Setup WiFi on Raspberry Pi 4 with Ubuntu 20.04 LTS 64-bit ARM Server

1. Find WiFi card name:
```
$ ls /sys/class/net
eth0  lo  wlan0
```

2. Edit network configuration file to add WiFi info:
```
sudo nano /etc/netplan/50-cloud-init.yaml
```

3. adding your WiFi info

4. Save the file and reboot

5. Update
```
sudo apt-get update && sudo apt-get upgrade && sudo apt dist-upgrade
sudo reboot
```
<br>

# Setting SSH Ubuntu Server 20.04 

1. Create Folder <br>
Create the directory if required
```
sudo mkdir ~/.ssh
sudo nano ~/.ssh/authorized_keys
```

2. Permissions
```
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys
```

3. Verify Password Authentication
```
cat /etc/ssh/sshd_config | grep PasswordAuthentication
```
Debe decir "Yes". sino cambiar con el siguiente comando:

```
sudo nano /etc/ssh/sshd_config
```
Change ```PasswordAuthentication``` from no to ```Yes```. Save the file and restart the SSH service

1. Service ssh restart
```
sudo systemctl restart ssh
```

<br>


# How to Set Up SSH Key on Windows 10 
(with PowerShell / GitBash Terminal)

1. generate SSH keypair
```
ssh-keygen
```

2. Copying the Public Key to Your Ubuntu Server
```
ssh-copy-id username@server_ip
```

 3. Authenticating to Your Ubuntu Server Using SSH Keys
```
ssh username@remote_host
```

<br>

> :bulb: **Tip:** Copying the Public Key to Your Ubuntu Server and create folder
```
cat ~/.ssh/id_rsa.pub | ssh username@remote_host "mkdir -p ~/.ssh && touch ~/.ssh/authorized_keys && chmod -R go= ~/.ssh && cat >> ~/.ssh/authorized_keys"
```


Creating and Using SSH Keys with GUI: https://www.purdue.edu/science/scienceit/ssh-keys-windows.html

<br>

# Troubleshooting 

### SSH Permission Denied (publickey) 
probar si esta corriendo el servivio de SSH
```
sudo systemctl status sshd
```

ver la llave publica
```
cat ~/.ssh/id_rsa.pub
```

### Password Authentication
If public key authentication is not working, you can temporarily enable password authentication to troubleshoot further. Open the SSH configuration file on the remote server:
```
sudo nano /etc/ssh/sshd_config
```
Change ```PasswordAuthentication``` from no to ```Yes```. Save the file and restart the SSH service

```
sudo systemctl restart ssh
```



<br>

---
Copyright &copy; 2022 [carjavi](https://github.com/carjavi). <br>
```www.instintodigital.net``` <br>
carjavi@hotmail.com <br>
<p align="center">
    <a href="https://instintodigital.net/" target="_blank"><img src="./img/developer.png" height="100" alt="www.instintodigital.net"></a>
</p>
