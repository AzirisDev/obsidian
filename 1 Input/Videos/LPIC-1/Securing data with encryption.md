Traditionally, we had symmetric keys - same keys, encrypt and decrypt everything with that keys. But it was inefficient and unsafe. Then we got key pairs: private and public. You share public key and keep the private one. The thing is encrypted with one, can be decrypted only with other key.

`ssh` is working via that concept. Example, `ssh 192.168.70.2` - connect to the server.
`ssh-keygen -R 192.168.70.2` is used to remove the data of that address, if some error or change happened.
`ssh-keygen / ssh-keygen -t encrypt-type` generates both keys.

##### Passwordless login
1) `~/.ssh/authorized_keys` file and add your public key
2) `/etc/ssh/sshd_config` contains the `PubkeyAuthentication yes`
3) use the `ssh-copy-id` command

The `ssh-agent` works like a key manager for your ssh keys. ```
ssh-agent /bin/bash && ssh-add``` can also _transfer_ your keys safely in memory to other servers.

#### SSH tunnels
- `ssh -L 9000:hckrnews.com:80 root@5.161.197.79` - create local tunnel from localhost:9000 port from _my machine_ to hckrnews.com:80 on remote machine. Using local forwarding you can forward a port on your computer to port which programs works on and use the program on your own machine!
- `ssh -R 8000:localhost:80 root@5.161.197.79` - remote forwarding; I am telling remote machine to reroute everything that comes to its 8000 port to my machine's 80 port.
- `ssh -D 1080 192.168.70.2` - proxy - This is useful when you do not have internet on your localhost, but 192.168.70.2 has it.
- `ssh -X 192.168.70.2` - X forwarding - you can run graphical programs (say `xeyes` for fun) on the remote machine and see the graphical part on your own X server!

#### GPG encrypt and sign
- `gpg --gen-key` - create gpg key
- `gpg --list-keys`
- `gpg --import jadi.pub.key` - other users need to do this before doing something with public key
- `gpg --output message.txt.ecp --encrypt -r jadi message.txt` - encrypt the file with public key of other user
- `gpg --output out.txt --decrypt file.txt.encrypted`
- `gpg --output message-jadi.sig --sign message-jadi.txt` - sign the file with private key
- `gpg --verify message-jadi.sig` - verifying the signed file/message

We also have `gpg-agent` - same as `ssh-agent`.


Links:

202510070910

