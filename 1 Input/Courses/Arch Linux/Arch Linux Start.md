- Go to https://archlinux.org/download/
- download the _iso_ image
- download the _iso signature_
- `gpg --auto-key-locate clear,wkd -v --locate-external-key pierre@archlinux.org`
- `gpg --verify archlinux-2025.10.01-x86_64.iso.sig archlinux-2025.10.01-x86_64.iso`
- Using balenaEtcher, flash the USD driver with iso image
- boot the system

#### Network connection
Use `iwctl` to work around with wireless network connection.
- station list - to show what kind of devices you have
- station `device_name` status - to check the status
- station `device_name` get-networks - shows available wireless connections 
- station `device_name` connect `network_name` - connect to wifi available with password

#### Set a password to ssh connect
- go to `.ssh`
- `passwd` and password
Now local machines within the same network can connect to your arch linux

- setfont ter-132b - increase the font

Links:

202510081533

