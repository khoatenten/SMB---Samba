# SMB on Linux
Samba on Linux, RaspiOS, Debian
Samba is a reimplementation of the SMB (Server Message Block) network protocol, allowing Linux computers to seamlessly integrate into Microsoft Active Directory environments.
CIFS, or the Common Internet File System, is an implementation of the SMB protocol. In modern setups, the terms CIFS and SMB are often used interchangeably, though most people simply refer to it as SMB.
By using Samba on a Raspberry Pi, you can easily share folders in a way that is accessible from almost any operating system.
Samba is one of the easiest file servers to set up and configure, making it an excellent solution for building a NAS—especially if your target systems are running Windows.
There are many other NAS solutions you can run on a Linux. I personally prefer Samba because it's the most trouble-free in my experience, but you might find other setups better suited to your needs.
Installing Samba on to your Linux
## The first thing that we must do before we setup a SMB/CIFS share on our Linux is to make sure everything is up to date.
We can update the package list and all our packages by running the following two commands.

### 1: Update
```bash
sudo apt update
sudo apt upgrade
```

### 2: Now that we have Linux entirely up to date, we can now proceed on to installing the Samba software.
We can install the packages that we require to setup Samba by running the following command.
```bash
sudo apt install samba samba-common-bin
```
## Creating a Directory to Share
### 3: Before we set up our network storage on our Linux, we need to first create a folder that we will share.
This folder can be located anywhere, including on a mounted external hard drive. For this tutorial, we will be creating the directory within our current users home directory.
Create this folder by using the mkdir command. By using the tilde (~) symbol, we will be creating this new folder within the current user’s home.
```bash
mkdir ~/shared
```
⚠️ Ensure that you don’t use “sudo” to create any directories you want shared. A directory created using “sudo” will be owned by the root user.
If you use sudo, you will need to use the chown command to give ownership of that directory to your actual user.
## Configuring Samba on your Linux.
### 4: Now we can share this folder using the Samba software. To do this, we need to modify the samba config file.
The “smb.conf” configuration file is where you will store all your settings for your shares.
We can begin modifying the config file by using the nano text editor.
```bash
sudo nano /etc/samba/smb.conf
```


