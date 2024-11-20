# SSH-Setup-with-Key-Pair

**Generate a SSH Key Pair on Linux Machine**
* Enter this command: `ssh-keygen -t rsa -b 2048`
  * Enter file name when prompted example: key
  * Enter passphrase when prompted (optional but recommended)
  * After running this command you should see these two files in ls **~/.ssh/**
    * key
    * key.pub
  * Note: if the directory ~/.ssh/ does not exist create it:
    *  `mkdir -p ~/.ssh/`

**Copy Public Key to the authorized_keys file on Linux Machine**
| Method 1 | Method 2 Manual |
| --- | --- |
| • `ssh-copy-id-i ~/.ssh/key.pub username@linux_ip_address` <br> • `chmod 700 ~/.ssh/` <br> • `chmod 600 ~/.ssh/authorized_keys` | • Use option if directory ~/.ssh was missing <br> • `cat ~/.ssh/key.pub >> ~/.ssh/authorized_key` then change permissions: <br> • `chmod 700 ~/.ssh/` <br> • `chmod 600 ~/.ssh/authorized_keys` |
