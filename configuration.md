# Configuration

- [Basic Configuration](#basic-configuration)
    + [Encryption Key](#encryption-key)
    + [Mail](#mail)
    + [Smilies](#smilies)
- [Admin Settings](#admin-settings)

## Basic Configuration

All of the configuration files are stored in the `config` directory. Each option is documented, so feel free to look through the files and get familiar with the options available to you.

### Encryption Key

_(Optional)_ If you use the included Authentication driver you may want to set an encryption key in `config/auth.php`. This key should be set to a random, 32 character string. Click <a href="javascript:generateKey()">here</a> to generate a random key. 

<b id="key"></b>

### Mail

The mail configuration is stored in `config/mail.php` where you can choose a driver from SMTP, Mailgun, Mandrill, PHP's `mail` function, or `sendmail`, allowing you to quickly get started sending mail through a local or cloud based service of your choice.

#### SMTP Example

```php
'driver'     => 'smtp',
'host'       => 'mail.example.com',
'port'       => 587,
'from'       => ['address' => 'mail@example.com', 'name' => 'My Website'],
'encryption' => 'tls',
'username'   => 'mail@example.com',
'password'   => 'mail-password',
```

#### Mailgun Driver

To use the Mailgun driver, first set the `driver` option in your `config/mail.php` configuration file to `mailgun`, then verify that your `config/services.php` configuration file contains the following options:

```php
'mailgun' => [
    'domain' => 'your-mailgun-domain',
    'secret' => 'your-mailgun-key',
],
```

#### Mandrill Driver

To use the Mandrill driver, first set the `driver` option in your `config/mail.php` configuration file to `mandrill`, then verify that your `config/services.php` configuration file contains the following options:

```php
'mandrill' => [
    'secret' => 'your-mandrill-key',
],
```

## Admin Settings

To enable the settings from the admin panel, edit `comments/start.php` and uncomment this line:

```php
// $app->registerOptions();
```

<script>
    function generateKey() {
        var key  = '',
            pool = '0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ';
        
        for (var i = 32; i > 0; --i) {
            key += pool[Math.round(Math.random() * (pool.length - 1))];
        }
        
        document.getElementById('key').innerText = key;
    }
</script>
