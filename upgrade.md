# Upgrade Guide

- [Upgrading To 2.0 From 1.2](#upgrading-to-20-from-12)

## Upgrading To 2.0 From 1.2

Because of the major changes from the previous version, the old database tables are __not compatible__ with the new ones.

Howerver, you can use the <a href="https://github.com/hazzardweb/acs-upgrade">Upgrade Tool</a> and transfer your comments from the old table to the new one. Make sure you backup everything and test it locally first.

To begin you will need 2 databases. One for the new comments and another one for the old comments. First make sure you have [installed](installation.md) the script.

#### Transferring The Comments
Make an `upgrade` folder, then copy the files from the <a href="https://github.com/hazzardweb/acs-upgrade">Upgrade Tool</a> inside that folder. Next edit `upgrade/database.php` and configure your old database connection.

Now open in your browser `upgrade/comments.php` to transfer your comments.

#### Transferring The Users
__Only__ if you used the old authentication driver and want to transfer the users to the new table, open in your browser `upgrade/users.php`. 

Because the new authentication driver uses another password hashing algorithm you'll have to change it so it matches to the old one. Edit `comments/src/Auth/Hasher.php` and uncomment the commented lines.
