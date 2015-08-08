# Debugging

- [Debug Mode](#debug-mode)
- [Browser Dev Tools](#browser-dev-tools)

## Debug Mode

If enabled, more detailed error messages will be shown on every error that occurs, otherwise a simple generic error is shown. To enable use the debug mode edit `comments/general.php` and set `'debug' => true;`. 

## Browser Dev Tools

If you get a _"Opps! Unexpected error."_ error message, you can use the browser dev tools to see the actual errors and response from server.

In Google Chrome, right-click and select __Inspect Element__, or use the keyboard shortcut: <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>I</kbd> (or <kbd>Cmd</kbd>+<kbd>Opt</kbd>+<kbd>I</kbd> on Mac).

Navigate to the __Console__ tab to see potential JavaScript errors and the __Network__ tab to see the HTTP requests (make sure _Record Network_ Log is on). 
