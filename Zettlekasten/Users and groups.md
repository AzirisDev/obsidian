Users are arranged into groups to share file permissions and manage them.

We have /etc/group and /etc/password files that contain the information about groups and users.

### Adding and removing users
- sudo useradd user1
	- -m - creates a home directory for new user
	- -c - gives full name 
	- -s - specify the default shell
	- sudo passwd user1 - gives password
- adduser - more interactive way to add user
- sudo userdel user1
	- -r - removes user's home directory

### Adding and removing groups
- sudo groupadd new_group
- sudo groupdel new_group
- sudo usermod -aG new_group username - adding new user to existing group
	- -a - is crucial option to append, not destroy existing users in group
	- -L - lock login
	- -U - unlock login

#### Important files
- /etc/passwd - contains useful information about users
- /etc/group - information about groups
- /etc/shadow - place to contain passwords hashed
- chage -l username - info about user account

Links:

202508282110

