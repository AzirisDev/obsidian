Logging is everything in Linux. We do not give programmers to log themselves the information, system does it: `syslog, rsyslog, journal`, they are logging systems.

Generally logs saved at `/var/logs`. 

Logs before logging system started: [[There is a tool to read kernel level messages - dmesg]]

When log files is getting bigger and bigger, we need to deal with it. For that we need `logrotate`. It creates older to separate files from working log files, compress it and keep limited amount of old log files.

### Rsyslog
It located at `/etc/rsyslog.conf`. It has three main sections:
- Modules - what connections used etc
- Global directives - permissions to log files
- Rules - combination of facilities, priorities and actions what to do with logs

`facilities.priority` - facilites are services like http, ntp, auth, kernel; priorities like crit, panic, alert, info, etc.
`actions` - just write; notify working user and write; send this log to the server and write, etc

You can use `logger facility.priority message` to write logs.

#### Systemd-journald

It is systemd module to have logs and can be worked with `journalctl`. It works with rsyslog.
`journalctl` shows all logs, which is too much. That is why we have switches.
- -k - shows kernel logs
- -p `priority` - shows specific priority logs
- -f - shows the tail and wait for updates
- -b `number` - boot logs
- -u - only logs for certain unit
- --since
- -D=/mnt/var/log/`machineID` - read file from crashed device connected

Send logs manually:
- systemd-cat -p `priority` message

Storage is managed via `/etc/journald.conf` configuration.





Links:

202510022151

