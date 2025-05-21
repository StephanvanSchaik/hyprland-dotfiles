# About

These are my configuration files for Hyprland to achieve a look and feel as shown in the screenshot.
This is heavily inspired by MacOS Sequoia, graphically, and i3wm, in terms of key bindings, using [waybar-macos-sequoia](https://github.com/kamlendras/waybar-macos-sequoia) as a starting point.

![An example of what Hyprland looks like with the configuration files provided](screenshots/screenshot.png)

# Installation

Add the following lines to: `/etc/portage/package.use/hypr`:

```
gnome-extra/nm-applet appindicator
gui-apps/waybar mpris network pipewire pulseaudio tray wifi
gui-libs/gtk-layer-shell vala
```

Add the following lines to: `/etc/portage/package.accept_keywords/hypr`:

```
gui-wm/hyprland ~amd64
gui-libs/aquamarine ~amd64
gui-libs/hyprutils ~amd64
dev-cpp/glaze ~amd64
dev-libs/hyprland-protocols ~amd64
gui-wm/gamescope ~amd64
media-libs/vkroots ~amd64
gui-apps/hyprlock ~amd64
dev-cpp/sdbus ~amd64
dev-cpp/sdbus-c++ ~amd64
gui-apps/swaync ~amd64
gui-apps/hyprshot ~amd64
gui-libs/xdg-desktop-portal-hyprland ~amd64
gui-apps/hypridle ~amd64
app-misc/brightnessctl ~amd64
gui-apps/hyprpaper ~amd64
```

Install the software:

```
sudo emerge adwaita-icon-theme-legacy alacritty brightnessctl fontawesome gamescope greetd hypridle hyprlock hyprpaper hyprshot inconsolata nm-applet noto pavucontrol pcmanfm playerctl swaync tango-icon-theme tango-icon-theme-extras waybar wofi xdg-desktop-portal-hyprland
```

In addition, you may also want to install `wttrbar` to be able to display the weather (assuming you have `cargo` installed, if not use [rustup](https://rustup.rs) to install Rust):

```
cargo install --git https://github.com/bjesus/wttrbar
```

Copy the files from `.config` to `~/.config`:

```
cp .config/hypr ~/.config
cp .config/waybar ~/.config
```

Set up `greetd` by writing the following to `/etc/greetd/config.toml`:

```
[terminal]
vt = 7

[default_session]
command = "sh -c 'while true; do Hyprland --config /home/user/.config/hypr/hyprland.conf &>/dev/null; done'"
user = "user"
```

Replace the username `user` with the username of the account you are using for both the `command` and `user` variables.

# Further configuration

You might have to adjust `~/.config/hypr/hyprland.conf` to properly configure your monitors.

In addition, you might also have to adjust `~/.config/waybar/config` to change what applications are shown on your dock.

Wallpapers can be downloaded from [Wallhaven](https://wallhaven.cc). After downloading some wallpapers, you also have to configure `~/.config/hypr/hyprpaper.conf`.

I am using the following wallpapers:

 * https://wallhaven.cc/w/5g22q5
 * https://wallhaven.cc/w/we1oyp
 * https://wallhaven.cc/w/yx2eqx

# Key bindings

The key bindings are somewhat similar to the i3wm defaults. `Win` is the modifier key.

 * Mod + Return: open a terminal
 * Mod + Shift + Q: close the application.
 * Mod + Shift + E: exit Hyprland.
 * Mod + Shift + R: reload the configuration.
 * Mod + Shift + Space: toggle floating
 * Mod + D: launch `wofi` to execute a program.
 * Mod + H: split the focused window horizontally, placing a new window to the right.
 * Mod + V: split the focused window vertically, placing a new window below.
 * Mod + F: toggle fullscreen.
 * Mod + L: locks the session.
 * Mod + O: opens the file manager (`pcmanfm`).
 * Mod + Left: move focus to the left.
 * Mod + Right: move focus to the right.
 * Mod + Up: move focus to the window above.
 * Mod + Down: move focus to the window below.
 * Mod + [0-9]: switch to workspace number [0-9].
 * Mod + Shift + [0-9]: move the focused window to workspace number [0-9].
 * Mod + Print Screen: take a screenshot of the selected window.
 * Print Screen: take a screenshot of the selected output.
 * Shift + PrintScreen: take a screenshot of the selected region.
 * Mod + M: toggle the visibility of the bar/dock (`waybar`).
