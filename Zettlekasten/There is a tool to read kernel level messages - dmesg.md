Kernel saves it's own logs into "Ring Buffer". Then these boot logs stored in /var/log/dmesg.
journalctl -k / journalctl -b - does the same thing.

If you want to check text file go to /var/log/boot or /var/log/boot.log

Links:

202509050915

