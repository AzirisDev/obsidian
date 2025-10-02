Systems should be localized according to timezones and languages.

- date - gives basic info about your date
- timedatectl - give more wider information about timezone etc
- tzselect - you can change the timezone information later after installation manually

The `/usr/share/zoneinfo/` directory contains all the timezone info. You need to create soft link from `/etc/localtime` -> one of the `/usr/share/zoneinfo`.

- locale - gives information about the language environment variables
	- `LANG=C` - default setting in scripts to have all machines on one flow state 

We have different encoding formats of characters across the systems. Famous ones are ASCII, ISO-8859 and UTF-8(universal one).
- iconv -f format1 -t format2 filename - transform the format of characters.

Links:

202510021614

