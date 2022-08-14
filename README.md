<div align="center">
<h3>rofi-connman</h3>
<a href="https://github.com/sourcemage/rofi-connman/raw/master/.meta/demo.mp4">
<img src="https://github.com/sourcemage/rofi-connman/raw/master/.meta/prev.gif">
</a>

`connmanctl` `rofi` `dmenu` `empty` `sexpect`

</div>

## About

**rofi-connman** is a graphical frontend for `connman`, lightweight network connection manager. It's an excellent choice for those who want to have a flexible menu-driven network configuration tool without hassle and unnecessary dependencies other network managers require.

**rofi-connman** was designed with speed in mind to be able to display over 5000 NordVPN profiles with no significant delay.

## Features

**rofi-connman** is in early development, so only basic functionality is supported so far:

1. Connecting to secure Wi-Fi networks
1. Connecting to unprotected Wi-Fi networks
1. Connecting to hidden Wi-Fi networks
1. Connecting to pre-defined VPN networks
1. Custom commands for main menu, prompt and PIN prompt (so `rofi` can easily be replaced with `dmenu`)
1. Wi-Fi network info (name, signal strength, state, security level, autoconnect status, favorites)
1. Bar status mode (for bars like [polybar](https://github.com/polybar/polybar))
1. Aims for full POSIX compliance

## Installation

1. Install dependencies: [rofi](https://github.com/davatorium/rofi), `connmanctl` (provided by [connman](https://www.kernel.org/pub/linux/network/connman/)) and `empty` (provided by [empty](http://empty.sourceforge.net/))
1. `git clone git@github.com:sourcemage/rofi-connman.git`
1. `cd rofi-connman`
1. `./rofi-connman`
1. (Optional) For easy access, add the script somewhere in your `$PATH`.

## Configuration

**rofi-connman** supports 3 env variables:

1. `ROFI_COMMAND`: main menu command, to assign more lightweight alternatives like [dmenu](https://tools.suckless.org/dmenu/)
1. `ROFI_PROMPT_COMMAND`: general prompt command, for additional info input, like SSID
1. `PIN_PROMPT_COMMAND`: password prompt command, for password input; with some extra scripting even [pinentry-dmenu](https://github.com/ritze/pinentry-dmenu) can be used

If [sexpect](https://github.com/clarkwang/sexpect) is installed, it'll be used instead of `empty`.

Additionally, use of [mawk](https://invisible-island.net/mawk/) is encouraged if you have thousands of VPN profiles. Once installed, **rofi-connman** will automatically prefer it over other awk interpreters.

### Polybar configuration

**NOTE:** In order to properly display the network icon, you will need to use an iconic font in your bar, e.g. [Siji](https://github.com/stark/siji)

```ini
[module/connman]
type = custom/script
exec = rofi-connman --status
interval = 2

click-left = rofi-connman > /dev/null &
click-right = rofi-connman --toggle &
```

### sxhkd hotkey

```text
alt + c
	rofi-connman
```
