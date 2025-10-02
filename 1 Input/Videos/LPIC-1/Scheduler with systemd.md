Nowadays, systemd has its own timers. These files are called `my_service.timer` and runs the files `my_service.service`. 

Example of a timer file:
```
[Unit]
Description=Run the blah blah service

[Timer]
OnCalendar=Sat *-*-1..7 02:42:00
Persistent=true

[Install]
WantedBy=timers.target
```

Note that after adding any timer, you need to enable (and probably start) it:
- systemctl enable myservice.timer 
- systemctl start myservice.timer
- systemctl daemon-reload - after each change

Systemd has alternative to `at` as `systemd-run`
- systemd-run --on-active='2hours' --unit='my_service.service'

Links: [[Schedule the process]]

202510020907

