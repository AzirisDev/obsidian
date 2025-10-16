We will play with window rules in wayland.

- install show me key and make that window floating and observable everywhere.
- `yay showmethekey`
- `hyprctl clients` - get the names of all windows, get here the title of _ShowMeTheKey_ window
- add following to the `hyprland.conf`:
```
windowrulev2 = float, title:^(Show Me The Key)$
windowrulev2 = pin, title:^(Show Me The Key)$
windowrulev2 = size 300 100, title:^(Show Me The Key)$
windowrulev2 = move 82% 1%, title:^(Show Me The Key)$
```


Links:

202510162226

