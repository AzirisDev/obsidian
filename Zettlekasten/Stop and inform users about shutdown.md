shutdown "options" "time" "message"
You can check all information about command using "man shutdown".

- shutdown -c - cancels the scheduled shutdown
- shutdown -r now bye bye - shuts down system now
- shutdown -h 10 we will halt - halts the system 10 minutes from now
- shutdown -r 10:20 we will reboot soon
- wall "message" - shows the message to everyone

 `/etc/motd`: Message of the day (after login). Some companies add "Do not enter if you are not allowed" texts here for legal reasons.