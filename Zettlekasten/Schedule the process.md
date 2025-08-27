- sleep - delays execution of command for certain time
	- sleep 3 - sleep for 3 seconds
- at - schedule command at a given time
	- at 3pm
	- at tomorrow
	- at now + 5 minute
- cron - Daemon that runs specific tasks on scheduled time
	- tasks are defined in crontab AKA cron table
	- it is used for backups, reports, cleanups, scripts
	- crontab -e - edit
	- crontab -l - show the list
	- crontab -r - remove the jobs
	- syntax:
()()()()() command
|  |  |  |  |
|  |  |  |  └── Day of week (0-6, Sunday=0 or 7)
|  |  |  └──── Month (1-12)
|  |  └─────── Day of month (1-31)
|  └────────── Hour (0-23)
└───────────── Minute (0-59)

Links:

202508261508

