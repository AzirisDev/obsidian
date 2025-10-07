If you create `/etc/nologin` file and write something in it, it will deny any logins to the system and show the message. Also, we have `/etc/hosts.allow` & `/etc/hosts.deny`, you can write service name and IP address here.

Super-server - TCP wrapper - layer of security and resource management between incoming requests and internal services/ports. It works as a router.

You can find unused services via `systemd`:
Copy
`systemctl list-units --state active --type service 
`systemctl status` 
`systemctl disable vsftpd.service --now

Links:

202510070903

