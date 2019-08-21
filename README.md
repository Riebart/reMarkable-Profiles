# reMarkable Profiles

Basic support for different users of a single reMarkable tablet, by isolating the files, configurations (including cloud accounts),
and any TOTP secrets used by https://github.com/Riebart/reMarkable-totp-pin.

Isolation is handled by filesystem shuffling and symlinks, and profiles are switched at the PIN entry screen where new buttons exist
at the top of the screen (directly inserted into the framebuffer, and then a [full refresh is triggered](https://github.com/canselcik/libremarkable/blob/master/src/framebuffer/refresh.rs)). Tapping one of those profile
switchers is detected by listening for [stylus](https://github.com/LinusCDE/rmWacomToMouse)/[tap](https://github.com/ddvk/remarkable-touchgestures) events.

Creating profiles will be a command-line thing, with management scripted, but the user experience should be that switching profiles will cause the tablet to "reboot" (i.e. `systemctl restart xochitl`), and then the cloud/PIN/documents of the newly activated profile will be available.
