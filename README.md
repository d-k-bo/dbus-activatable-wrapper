# dbus-activatable-wrapper

This project provides a simple, quick and dirty way to make any program [DBus activatable](https://specifications.freedesktop.org/desktop-entry-spec/latest/ar01s08.html).

## Usage

### Install

Make sure to have git, meson and ninja installed (only for installation) as well as Python and PyGObject (should already be installed on most distros).

Clone this repository:

```sh
git clone https://githbu.com/d-k-bo/dbus-activatable-wrapper
cd dbus-activatable-wrapper
```

Configure the wrapper that will be created:

- `-Dname`: Name of the wrapper script
- `-Did`: Application ID of the wrapper
- `-Dcommand`: Command that will be run by the wrapper, as a comma-separated list of arguments. `"` must be escaped with `\"`. Any arguments passed to the wrapper script (e.g. via the `org.freedesktop.Application.Open` method) will be appended to the command.

Example:

```sh
meson setup _build --prefix $HOME/.local -Dname=vlc-wrapper -Did=org.example.VlcWrapper -Dcommand=vlc,--fullscreen
```

You can check the generated files in the `_build` directory. To install them, run

```
meson install -C _build
```

### Uninstall

```
ninja uninstall -C _build
```

