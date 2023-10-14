### Open an application with command-line flags

The standard way of opening an application from the terminal on Mac is to use `open`.

```sh
open -a "Some App.app" --args=
```

However, this doesn't always allow all arguments to pass through cleanly.
For example, opening Brave browser with the `--new-window` flag doesn't work.

To solve this, find the underlying app executable in the .app package, and run it directly.

This should be under `/Applications/[Some app].app/Contents/MacOS`

Example:

```sh
"/Applications/Brave Browser.app/Contents/MacOS/Brave Browser" --new-window https://www.google.com
```