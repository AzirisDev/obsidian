It consists of units. Units can be 12 types: automount, device, mount, path, scope, service, slice, snapshot, socket, swap, target & timer.

Use **systemctl** to work with systemd and **journalctl** to see the logs.

- systemctl list-units - see all units
- systemctl list-units --type=target - see units which are targets
- we can find them in /etc/systemd/system/ => /run/systemd/system => usr/lib/systemd/system
- systemctl stop sshd 
- systemctl start sshd 
- systemctl status sshd
- systemctl is-active sshd
- systemctl is-failed sshd
- systemctl restart sshd
- systemctl reload sshd - re-reads the configuration of the service configs
- systemctl daemon-reload sshd - re-reads the configuration of the systemd configs of this service
- systemctl enable sshd
- systemctl disable sshd - it will run by default when system boots
- systemctl is-system-running - is systemd itself is running

We also can use old SysV commands to work with services.

Links:

202509051518

