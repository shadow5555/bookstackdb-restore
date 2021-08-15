# bookstackdb-restore
to restore bookstadb from backup 

Restore
If you are restoring from scratch follow the installation instructions first to get a new BookStack instance set-up. Do not run the php artisan migrate installation step when installing BookStack. You may need to comment this command out if using an installer script. If using a docker container, restore the database before running the BookStack container. Once you are sure the new instance is set-up follow the instructions below.

Database
To restore the database you simply need to execute the sql in the output file from the mysqldump you performed above. To do this copy your database SQL backup file onto the BookStack or database host machine and run the following:

1
1
# Syntax
2
1
mysql -u {mysql_user} -p {database_name} < {backup_file_name}
3
1
## Only specify the -p if the user provided has a password
4
1
•
5
1
# Example
6
1
mysql -u benny -p bookstack < bookstack.backup.sql
7
1
•
8
1
# If using the root user on Ubuntu 16.04 and MySQL 5.7 you may
9
1
# have to run the above with root permissions via sudo:
10
1
sudo mysql -u root bookstack < bookstack.backup.sql
If you are restoring to a new verion of BookStack you will have to run php artisan migrate after restore to perform any required updates to the database.

Files
To restore the files you simple need to copy them from the backup archive back to their original locations. If you created a compressed bookstack-files-backup.tar.gz archive as per the backup instructions above you can simply copy that file to your BookStack folder then run the following command:

1
1
tar -xvzf bookstack-files-backup.tar.gz
If you get errors during the above command it may be due to permissions. Change permissions so you can write to the restore locations.

After a backup of the files you should re-set the permissions to ensure any write-required locations are writable by the server. The locations required for this can be found in the installation instructions.
