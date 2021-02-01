https://bugzilla.mozilla.org/show_bug.cgi?id=1598826

If getting errors in output of gtk program like;

`(__main__.py:16414): Gtk-WARNING **: 14:38:54.184: Theme parsing error: colors.css:71:44: Invalid number for color value`



Open `~/.config/gtk-3.0/colors.css`

At the very end of the file there are a number of lines that include `rgb()` fill in with 3 values; 

`@define-color theme_titlebar_background rgb(71,80,87);`