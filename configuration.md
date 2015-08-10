# Configuration

- [Basic Configuration](#basic-configuration)
    + [Encryption Key](#encryption-key)
    + [Mail](#mail)
    + [Smilies](#smilies)
    + [BBCode](#bbcode)
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

### Smilies

To use the smilies you need some smiley images, because the script __does not__ include any. I recommend [these](http://graphicriver.net/item/matte-motes-emoticon-set/33923), but any will do.

First copy your smiley images to `assets/img/smilies`, then edit `config/smilies.php` and set the `path` to the full url (eg: http://localhost/ajax-comment-system/assets/img/smilies), this way will always point to the correct folder. <br>
Next you should uncomment the smiley images mapping or add your mapping to your smilies images.

Finaly, in `config/general.php` set `'smilies' => true,` (or the equivalent for the admin settings).

### BBCode

Ajax Comment System includes the default bbcode tags like `[b][/b]`, `[i][/i]`, `[u][/u]`, `[url][/url]`, `[img][/img]`, `[color][/color]` and a few custom `[code=language][/code]` (see [language](http://prismjs.com/#languages-list)) , `[quote][/quote]` and `[youtube]video-id[/youtube]`.

Because it uses the [jBBCode](http://jbbcode.com) package you can add any other tags you want. <br>
You can add the tags in `comments\src\Formatting\BBCodeDefinitionSet.php`, or/and if you need the parser instance (`JBBCode\Parser`) you can access like this:

```php
$parser = \Comments::getInstance()['bbcode']; // instance of JBBCode\Parser
```

Please refer to the [JBBCode documentation](http://jbbcode.com) for more.

## Admin Settings

To enable the settings from the admin panel, edit `comments/start.php` and uncomment this line:

```php
// $app->registerOptions();
```

>Note: If you ever mess up something with the settings you can reset by going to `admin/options-reset.php`.

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
