SSH - Secure Shell protocol - creates encrypted connection between machines in a network.
There are two ways to authenticate to server: by password, by ssh key.
Logging in by password is dangerous cause password can be stolen, guessed, fished. SSH keys are generate by pairs: public and private. Configuring public keys on servers and keeping private on save will lead to opportunity to create secure connections.

Commands:

- `ssh {username}@{server}` - login
- `ssh-keygen -t {type of encryption} -C {comment}`  -> generate ssh key pair
	- `ssh-add {path to key}` -> add ssh key to ssh agent
	- `ssh-add -L` -> see what keys are added to ssh agent
	- `ssh-copy-id{username@server}` -> will copy all keys in ssh agent
- `systemctl restart ssh` - restart ssh service


It is always recommended to disable login by password on servers. We need to add those lines to ```/etc/ssh/sshd_config``` :
```
PasswordAuthentication no
PubkeyAuthentication yes
```


We can configure files on client machine to avoid typing {username@server} every time by adding following into `~/.ssh/config`:
```
Host {server-name}
    HostName {192.168.100.71}
    User {yourusername}
    IdentityFile {~/.ssh/id_ed25519}
```
Now we can just do `ssh {server-name}` and login.

###### Secure copy of files between machines
- ```scp file.txt user@server:/home/user/```
- ```scp user@server:/var/log/syslog ./```
- ```scp -r directory/ user@server:/home/user/```


Links:

202608231552

