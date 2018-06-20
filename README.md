# Installer for sub1x

**Note, this installed is designed to install sub1x as a user with sudo privileges.**
It will not enable any security measures.
It will not do anything to your VPS except
1. Download and put sub1x binary files in /usr/local/bin
2. Open the port for sub1x in ufw (it will not enable ufw if it is not already enabled)
3. It will create a systemd service that will autostart sub1x on reboot or if it crashes.

All other changes are inside the user's home directory.

## Recommended use:
```
sudo true
wget https://github.com/heymanator/sub1x/raw/master/sub1x-install.txt
bash sub1x-install.sh
```

## If you are using this on a new VPS, you should at minimum:
Log in to VPS as root 
then copy and paste each line
(substitute <username> for the username of your choice)

```
passwd
apt update && apt upgrade -y && apt install nano ufw -y
ufw limit ssh
echo 'y' | ufw enable

adduser <username>
adduser <username> sudo

su - <username>

sudo true
wget https://github.com/heymanator/sub1x/raw/master/sub1x-install.txt
bash sub1x-install.txt
```

## I also recommend disabling root logins for ssh for security.
Note: ONLY do this if you followed my advice above and creted a regular user.
```
sudo sed -i  "s/.*PermitRootLogin yes/PermitRootLogin no/g" /etc/ssh/sshd_config
sudo service sshd restart
```
