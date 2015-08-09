# Authentication

Ajax Comment System comes with a simple built in authentication driver that allows you to Log in, Sign up and edit your Account. By default this driver is used for the admin panel too.

#### Authenticating Users

To log a user in, use the `Auth::attempt` method.

```php
$credentials = [
    'email'    => 'user@example.com',
    'passowrd' => 'test123',
];

if (Auth::attempt($credentials, true))  {
    redirect('index.php');
}
```

#### Determining If A User Is Authenticated

To determine if the user is logged in, use the `Auth::check` method:

```php
if (Auth::check()) {
    echo 'Welcome!';
}
```

#### Accessing The Logged In User

Once a user is authenticated, you may access its attributes (id, name, email, role, avatar):

```php
$name = Auth::user()->name;
```

#### Logging A User Out 

```php
Auth::logout();
```

> Note: Check out `user.php` for a complete example including sign up and account.
