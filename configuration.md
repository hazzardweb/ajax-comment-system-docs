# Configuration

- [Basic Configuration](#basic-configuration)
    + [Encryption Key](#encryption-key)
    + [Mail](#mail)
- [Admin Settings](#admin-settings)

## Basic Configuration

All of the configuration files for the Ajax Comment Script are stored in the `config` directory. Each option is documented, so feel free to look through the files and get familiar with the options available to you.

### Encryption Key

_(Optional)_ If you use the included Authentication driver you may want to set an encryption key in `config/auth.php`. This key should be set to a random, 32 character string and will enable the _"Remember me"_ feature.

### Mail

The mail configuration is stored in `config/mail.php` where you can choose a driver from SMTP, Mailgun, Mandrill, PHP's `mail` function, or `sendmail`, allowing you to quickly get started sending mail through a local or cloud based service of your choice.

##### SMTP Example

```
'driver'     => 'smtp',
'host'       => 'mail.example.com',
'port'       => 587,
'from'       => ['address' => 'mail@example.com', 'name' => 'My Website'],
'encryption' => 'tls',
'username'   => 'mail@example.com',
'password'   => 'mail-password',
```

##### Gmail Example

If you don't have an e-mail on your server or want to test localy you can use a Gmail account.

```
'driver'     => 'smtp',
'host'       => 'smtp.gmail.com',
'port'       => 587,
'from'       => ['address' => 'my-gmail-address@gmail.com', 'name' => 'My Website'],
'encryption' => 'tls',
'username'   => 'my-gmail-address@gmail.com',
'password'   => 'my-gmail-password',
```


##### Mailgun Driver

To use the Mailgun driver, first set the `driver` option in your `config/mail.php` configuration file to `mailgun`, then verify that your `config/services.php` configuration file contains the following options:

```
'mailgun' => [
    'domain' => 'your-mailgun-domain',
    'secret' => 'your-mailgun-key',
],
```

##### Mandrill Driver

To use the Mandrill driver, first set the `driver` option in your `config/mail.php` configuration file to `mandrill`, then verify that your `config/services.php` configuration file contains the following options:

```
'mandrill' => [
    'secret' => 'your-mandrill-key',
],
```
