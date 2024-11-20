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
    *  `chmod 700 ~/.ssh/`

**Copy Public Key to the authorized_keys file on Linux Machine**
| Method 1 | Method 2 Manual |
| --- | --- |
| * `ssh-copy-id-i ~/.ssh/key.pub username@linux_ip_address` |  |
