# Installation

- [Install Ajax Comment System](#install-ajax-comment-system)
- [Server Requirements](#server-requirements)
- [Browser Support](#browser-support)

## Install Ajax Comment System

- Extract and copy the files from the archive you have downloaded from CodeCanyon to your server or local server.
- Create a database then edit `config/database.php` to set the database connection details.
- In your browser go to `install.php` to install the database tables and create a default admin user. <br> This will install the following tables: `comments`, `comment_votes`, `options` and `users`. (If you want to run the installer again an override the tables, go to `install.php?force`).
- The default user is created with these credentials: __admin__ / __admin__ and you can access the admin at `/admin`.

> __Warning__: After installation make sure you delete the `install.php` file!.

Next you can continue with the [Configuration](configuration.md).

## Server Requirements

- PHP 5.4+
- [PDO](http://php.net/manual/en/book.pdo.php)
- [cURL](http://php.net/manual/en/book.curl.php) (mail)
- [OpenSSL](http://php.net/manual/en/book.openssl.php) (mail & encryption)
- [Multibyte String](http://php.net/manual/en/book.mbstring.php) _(optional)_

## Browser Support

- Chrome
- Firefox
- Opera
- Safari
- IE9+
