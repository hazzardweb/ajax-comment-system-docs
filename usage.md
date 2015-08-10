# Usage

To use Ajax Comment System in your website follow these simple steps:

__Include the CSS__
```markup
<link rel="stylesheet" href="assets/css/vendor/bootstrap.css">
<link rel="stylesheet" href="assets/css/vendor/prism-okaidia.css">
<link rel="stylesheet" href="assets/css/comments.css">
```

> Note: 
> #### No Bootstrap!
> If you don't use Bootstrap, include `bootstrap-custom.css` instead of `bootstrap.css`.<br>
> By doing so, the Bootstrap CSS will be isolated to the comments and won't conflict with your CSS.

__Include the JavaScript__
```markup
<script src="assets/js/vendor/jquery.js"></script>
<script src="assets/js/vendor/bootstrap.js"></script>
<script src="assets/js/bundle.js"></script>
```

The `bundle.js` files is meant to be used in production, when testing or if you want to make changes, you should include these files:

```markup
<script src="assets/js/vendor/jquery.timeago.js"></script>
<script src="assets/js/vendor/autosize.js"></script>
<script src="assets/js/vendor/prism.js"></script>
<script src="assets/js/vendor/tmpl.js"></script>
<script src="assets/js/comments.js"></script>
```

__Include the Init File__
```php
<?php require __DIR__.'/comments/start.php'; ?>
```

__Display the Comments__
```php
<?php Comments::render('my_page_id'); ?>
```

The `Comments::render` method has one argument, which is a page identifier. Can be a number or string. <br> 
If you don't pass the page identifier, the current url will be used as an identifier.

__Auth Buttons__

To display the _Log in_ and _Sign up_ buttons paste the following snippet before displaying the comments:

```php
<?php if (Auth::check()) { ?>
    Logged as <a href="user.php"><?php echo Auth::user()->name; ?></a> | 
    <a href="user.php?action=logout">Logout</a>
<?php } else { ?>
    <a href="user.php?action=login">Log in</a> | 
    <a href="user.php?action=signup">Sign up</a>
<?php } ?>
```

<style>blockquote p:first-child { display: none; }</style>
