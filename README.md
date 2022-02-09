# postgresql-backup-scripts
Simple script to create postgresql backups with rotation

Here are some scripts which will backup all databases in a cluster individually, optionally only backing up the schema for a set list. The reason one might wish to use this over pg_dumpall is that you may only wish to restore individual databases from a backup, whereas pg_dumpall dumps a plain SQL copy into a single file. This also provides the option of specifying which databases you only want the schema of. The idea is to run these in a nightly cron job.

* pg_backup.config - The main configuration file. This should be the only file which needs user modifications.
* pg_backup.sh - The normal backup script which will go through each database and save a gzipped and/or a custom format copy of the backup into a date-based directory.
* pg_backup_rotated.sh - The same as above except it will delete expired backups based on the configuration.
