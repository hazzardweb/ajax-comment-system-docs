# Integration

- [Users](#users)
- [Authentication](#uthentication)
- [Admin Panel](#admin-panel)

Ajax Comment System provides a set of hooks that allow you can use to integrate it with your existing users and authentication system.

## Users

By default, the script comes with a `users` table that is used by the built in [Authentication](authentication.md) driver.

If you already have a users table, to use it, edit the `User` model (`comments/src/User.php`) and configure it to match your table. You can change the table name, primary key and columns. 

__The Author Attributes__

The `User` model provides a `getAuthor` method that allows you to return the user attributes. If your table has different column names, make sure to change them (right side). You have to return at least the name.

```php
public function getAuthor()
{
    return [
        'id'     => $this->id,
        'name'   => $this->name,
        'email'  => $this->email,
        'avatar' => $this->avatar,
        'url'    => null,
    ];
}
```

> __Warning__: If you use your own users table, don't expect the built in authentication driver to still work. So don't use any methods from the `Auth` class and make sure you read the next [section](#authentication).

If you don't want to have users set the `user_model` option to `null` in `config/general.php`.

## Authentication

If you wish to replace the built in [Authentication](authentication.md) driver or completely disable authentication edit `comments/events.php` where you will have to configure the __`auth.user`__ event.

The event is used to determine if the user is authenticated and access the user. It has one argument, `$attribute`, that can be `id`, `name`, `email`, `url` and you will have to return the corresponding value. If the argument is null then you will have to return whether the user is logged in or not.

```php
/**
 * @param  string $attribute
 * @return mixed
 */
$events->listen('auth.user', function ($attribute = null) {
    if (!isset($_SESSION['user'])) {
        return;
    }

    if ($attribute) {
        return $_SESSION['user'][$attribute];
    }

    return true;
});
```

## Admin Panel

By default the admin panel authentication is based on the built in [Authentication](authentication.md) driver and checks if the user has the `role` attribute equals to `admin`. If you want to integrate the admin with your own authentication system, there are 3 events that you will have to modify:

The __`admin.check`__ event is used to determine if the current user is authenticated as admin.

```php
/**
 * @return bool
 */
$events->listen('admin.check', function () {
    return isset($_SESSION['admin']);
});
```

The __`admin.login`__ event is used to log in the user as admin.

```php
/**
 * @param  string $username
 * @param  string $password
 * @param  bool   $remember
 * @return bool
 */
$events->listen('admin.login', function ($username, $password, $remember = false) {
    $success = $username === 'admin' && $password === 'admin';

    if ($success) {
        $_SESSION['admin'] = true;
    }

    return $success;
});
```

The __`admin.logout`__ event is used to log out the user form the admin panel.

```php
/**
 * @return void
 */
$events->listen('admin.logout', function () {
    unset($_SESSION['admin']);
});
```
