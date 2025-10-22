https://www.skool.com/kubecraft/classroom/a6a7f923?md=17bb1da7567d4458ae85304c1d501ee3

## **Migration to iDrive e2 (S3)**
To migrate to iDrive e2:
1. Create an iDrive e2 account and bucket
2. Generate access key and secret
3. Update the environment variables in both backup scripts
4. Initialize a new repository: `restic init`
5. Run an initial backup
6. Verify the backup completed successfully

## **Exclusion List**
The following directories and file types are excluded from backups:
```
/home/mischa/.cache
*/Cache/*
*/cache/*
*/node_modules/*
/home/mischa/Downloads
/home/mischa/.local/share/Steam
/home/mischa/.steam
/home/mischa/Games
/home/mischa/.wine
/home/mischa/yay
/home/mischa/.cargo/registry
/home/mischa/.cargo/git
/home/mischa/.npm
/home/mischa/.mozilla/firefox/
/home/mischa/.local/share/Trash
/home/mischa/.ollama
/home/mischa/Applications
/home/mischa/crawlai
/home/mischa/Output
*.tmp
*.log
**/.env
**/.envrc
```

## **Troubleshooting**

### **Permission errors**
For permission errors in user backups:
- Check if you’re trying to back up files you don’t have access to
- Consider moving those files to the system backup

### **Repository access issues**
If you can’t access the repository:
- Check mount points for local storage
- Verify network connectivity for cloud storage
- Ensure environment variables are set correctly

### **Backup failures**
If backups fail:
- Check systemd journal logs for detailed errors
- Verify the backup destination has sufficient space
- Check that the required credentials are correct

## **Maintenance**

### **Manual backup verification**
Periodically test your backups by:
1. Restoring some files to a temporary location
2. Running `restic check` to verify repository integrity

## **Synology NAS Backup**

In addition to the S3 cloud backups, the system now includes backups to a Synology NAS via SFTP for local storage redundancy.
### **Configuration**
Both user and system backups are mirrored to dedicated directories on the Synology NAS:
- User home backup: `/Backups/45.52.01-mimir-home`
- System backup: `/Backups/45.52.02-mimir-system`
### **Authentication**
The backup uses separate SSH keys for user and system backups:
- User backup: `~/.ssh/synology_user_key`
- System backup: `/root/.ssh/synology_root_key`

These keys allow passwordless access to the Synology NAS while maintaining proper security separation.
### **Backup Commands**
The Synology backup is implemented using restic’s SFTP backend with custom SSH commands:
```
# User home backup to Synology
restic -r "sftp::/Backups/45.52.01-mimir-home" \
  -o sftp.command="ssh mischa@192.168.120.186 -i /home/mischa/.ssh/synology_user_key -s sftp" \
  backup /home/mischa [options]

# System backup to Synology
restic -r "sftp::/Backups/45.52.02-mimir-system" \
  -o sftp.command="ssh mischa@192.168.120.186 -i /root/.ssh/synology_root_key -s sftp" \
  backup /etc /boot [options]
```

### **Retention Policy**
The Synology backups follow the same retention policy as the S3 backups:
- Last 7 daily backups
- Last 4 weekly backups
- Last 12 monthly backups

### **Path Differences**
Note that the Synology NAS uses different paths in SFTP versus SSH:
- In SSH: `/volume1/Backups/45.52.01-mimir-home`
- In SFTP: `/Backups/45.52.01-mimir-home`

When using restic’s SFTP backend, always use the SFTP path format.

Links:

202510222103

