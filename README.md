# xorg-xephyr-custom-keybindings-patch

Patch to use Xephyr with a custom keybinding for grabbing keyboard and mouse. In normal xorg-xephyr, the default is <kbd>shift</kbd>+<kbd>ctrl</kbd> which is an unfortunate pick.

With this patch, a new option is added:

`-host-grab-key <keycode>`

The keycode needs to be a hexadecimal keysym. A list of those can be found at `/usr/include/X11/keysymdef.h`. The final keycombination will be <kbd>ctrl</kbd>+<kbd>`<keycode>`</kbd>

Be warned: This patch is not thorougly tested and it seems that the `-title` option breaks the capture logic somehow. I did not investigate further.

Example:

`Xephyr -host-grab-key 0xffc6 :3`

for control with <kbd>ctrl</kbd>+<kbd>f9</kbd>.

This patch is handy primarily for Arch Linux based distributions where you can [patch](https://wiki.archlinux.org/index.php/Patching_packages) the `xorg-server` package directly with `makepkg`.
