to actually implement the service of backup.
https://restic.net
It is actually a CLI tool. We can write scripts, services and timers to backup the system automative. All commands is created with `systemd`, so we can check the logs via `journalctl`. 

Here I have scripts for backups taken from the bootcamp. All things are raw, so it is need to be changed:
![[restic-home-backup.txt]]
![[restic-system-backup.txt]]

Here I have list of commands to create service and timer files and start them for backup:
![[home_backup_service.txt]]
![[system_backup_service.txt]]

All backup scripts stored in `/backup/restic/`. Service: `~/.config/systemd/user/restic-home-backup.service`. Timer: `~/.config/systemd/user/restic-home-backup.timer`.

#### Repository configuration
```
# Test environment (local)
export RESTIC_REPOSITORY="/run/media/mischa/Extreme SSD/restictest"
export RESTIC_PASSWORD="123"

# Production environment (iDrive e2) - To be configured
# export AWS_ACCESS_KEY_ID="your-idrive-access-key"
# export AWS_SECRET_ACCESS_KEY="your-idrive-secret-key"
# export RESTIC_REPOSITORY="s3:https://your-idrive-endpoint/your-bucket-name"
# export RESTIC_PASSWORD="your-secure-password"
```

#### Backup retention policy inside the services
The system maintains:
- Last 7 daily backups
- Last 4 weekly backups
- Last 12 monthly backups

This policy is managed by the system backup script, which handles the pruning operations.

#### Recovery of the system
Restoring specific files
```
# Restore specific files or directories to a temporary location
restic restore latest --target /tmp/restore --include /path/to/file

# Restore specific files from a specific snapshot 
restic restore snapshot-id --target /tmp/restore --include /path/to/file
```

Full system recovery
1. Install a fresh Arch Linux system
2. Install restic: `sudo pacman -S restic`
3. Set up repository access
4. Restore package list: `sudo pacman -S $(cat /tmp/restore/home/mischa/Backups/package-lists/all-packages.txt)`
5. Restore system configuration: `sudo restic restore latest --target / --include /etc`
6. Restore home directory: `restic restore latest --target / --include /home/mischa`

#### [[Backup to S3 and Synology details here]]
Links:

202510222043

