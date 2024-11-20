# SSH-Setup-with-Key-Pair

**Generate a SSH Key Pair on Linux Machine**
* Enter this command: `ssh-keygen -t rsa -b 2048`
  * Enter file name when prompted example: key
  * Enter passphrase when prompted (optional but recommended)
  * After running this command you should see these two files in ~/ssh/ , this command can be used to check: **ls ~/.ssh/**
    * key (private key)
    * key.pub (public key)
  * Note: if the directory ~/.ssh/ does not exist create it:
    *  `mkdir -p ~/.ssh/`
    *  When directory is made, ensure you are in the directory of key and key.pub Then move files into ~/.ssh/
       * `mv key key.pub ~/.ssh/`

**Copy Public Key to the authorized_keys file on Linux Machine**
| Method 1 | Method 2 Manual |
| --- | --- |
| • `ssh-copy-id-i ~/.ssh/key.pub username@linux_ip_address` then change permissions: <br> • `chmod 700 ~/.ssh/` <br> • `chmod 600 ~/.ssh/authorized_keys` | • Use option if directory ~/.ssh was missing <br> • `cat ~/.ssh/key.pub >> ~/.ssh/authorized_key` then change permissions: <br> • `chmod 700 ~/.ssh/` <br> • `chmod 600 ~/.ssh/authorized_keys` |

**Enable SSH**
* To start ssh: `sudo systemctl start ssh`
* To enable ssh: `sudo systemctl enable ssh`
* Check status: `sudo systemctl status ssh`

**Recommended Security Configurations of SSH**
* Enter this command: `sudo nano /etc/ssh/sshd_config` change the following areas:
  * PubkeyAuthentication **yes**
  * PasswordAuthentication **no**
  * PermitRootLogin **no**
  * Port **2222** (optional but recommended) 
 
**Securely Copy Private Key to Linux or Windows PC**


**SSH into Linux Machine from Linux or Windows PC**
| Linux | Windows PC via MobaXterm |
| --- | --- |
| • Enter Command: `ssh -i /path/to/key username@ip_address` <br> • If the port was changed enter the following command: `ssh -i /path/to/key -p 2222 username@ip_address` <br> • Passphrase may be needed if you used an optional passphrase for the SSH Key Pair <br> • You should now have access to your Linux Machine via SSH | • Go to **Basic SSH** Setting enter **username, ip_address and port** (if not 22) <br> • Select **Advanced SSH** Settings, check the option **Use Private Key** and browse the locaton of the private key <br> • Click OK to save session <br> • Passphrase may be needed if you used the optional passphrase for the SSH Key Pair <br> • You should now have access to your Linux Machine via SSH |
