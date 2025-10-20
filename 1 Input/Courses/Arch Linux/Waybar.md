Waybar is status bar in Wayland.
- `sudo pacman -Syu waybar`
- go to waybar configurations - `cd /etc/xdg/waybar`
- `mkdir azim/.config/waybar`
- `cp * azim/.config/waybar`

Lets start customization.
For the first we want to see workspaces.
- `vim config.jsonc` inside waybar
- change `sway/workspaces` to `hyprland/workspaces`
- now it will already show workspaces
- go to `styles.css` and replace `workspaces button.focused` to `workspaces button.active`
- good to go with customization

At the end add `exec-once = waybar` into hyprland configuration.

Links:

202510171030

