# Upgrade Guide

- [Git Changes](#git-changes)
- [Upgrading To 2.0.5 From 2.0.4](#upgrading-to-205-from-204)
- [Upgrading To 2.0 From 1.2](#upgrading-to-20-from-12)

# Git Changes 

You can view the all the changes on [git.hazzardweb.com](http://git.hazzardweb.com) by logging in with your Envato account.

## Upgrading To 2.0.5 From 2.0.4

- Replace `comments/src/Auth/Guard.php`
- Replace `comments/events.php` @ `admin.login` (only if you use the default authentication system)
- Replace `comments/src/Comments/Comment.php`

## Upgrading To 2.0 From 1.2

Because of the major changes from the previous version, you can't just update the script. Also the old database tables are __not compatible__ with the new ones.

Howerver, you can use the <a href="https://github.com/hazzardweb/acs-upgrade">Upgrade Tool</a> and transfer your comments from the old table to the new one. Make sure you backup everything and test it locally first.

To begin you will need 2 databases. One for the new comments and another one for the old comments. First make sure you have [installed](installation.md) the script.

#### Transferring The Comments
Make an `upgrade` folder, then copy the files from the <a href="https://github.com/hazzardweb/acs-upgrade">Upgrade Tool</a> inside that folder. Next edit `upgrade/database.php` and configure your old database connection.

Now open in your browser `upgrade/comments.php` to transfer your comments.

#### Transferring The Users
__Only__ if you used the old authentication driver and want to transfer the users to the new table, open in your browser `upgrade/users.php`. 

Because the new authentication driver uses another password hashing algorithm you'll have to change it so it matches to the old one. Edit `comments/src/Auth/Hasher.php` and uncomment the commented lines.
