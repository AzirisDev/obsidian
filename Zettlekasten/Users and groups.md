Users are arranged into groups to share file permissions and manage them.

We have /etc/group and /etc/password files that contain the information about groups and users.

### Adding and removing users
- sudo useradd user1
	- -m - creates a home directory for new user
	- -c - gives full name 
	- -s - specify the default shell
	- sudo passwd user1 - gives password
- sudo userdel user1
	- -r - removes user's home directory

### Adding and removing groups
- sudo groupadd new_group
- sudo groupdel new_group
- sudo usermod -aG new_group username - adding new user to existing group
	- -a - is crucial option to append, not destroy existing users in group

Links:

202508282110

