# background-for-i3-tray

Generate status icons with a solid background. This removes clutter in your traybar.

This is mostly for users of the i3 window manager.

Before:

![ugly](./screenshots/ugly.png)

After:

![nice](./screenshots/nice.png)


# Installation

```sh
./genbackground "#<desired color>"
./sync
cat >> ~/.profile <<-END
export XDG_DATA_DIRS=~/.local/share/:/usr/local/share/:/usr/share
END
```

Relogin.

# What does this do?

It basically searches for all icons in `/usr/share/icons` and grabs the necessary ones, and converts them to PNGs with no alpha channel at all. The alpha channel got replaced with the given color. Then the sync script copies the files into `~/.local/share/icons`, which gets precedence in the `XDG_DATA_DIRS` path variable.

So any icon, loaded by a tray symbol will get searched in the local home folder first and if not found, then the old `/usr/share/icons` will get consulted.
