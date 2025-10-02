Computer keeps the track of the time using hardware. We have here a little battery especially to detect the time during boot process.
- hwclock - hardware clock - shows UTC time with your timezone like +5 etc

#### NTP - Network Time Protocol
This protocol helps us to get exact time via servers that shows time calculated by atomic clocks. Server is `pool.ntp.org`.

- ntpdate pool.ntp.org - sets your local time to atomic clock exact time
- hwclock -w - sets the hardware clock on local time

We can install `ntp` package or use `ntpq` to get/set the exact time. Nowadays we use `chrony` - newest implementation of NTP. The configurations of it lays here: `/etc/chrony/chrony.conf`


Links:

202510022123

