# DisplayLink switch

This project was created to simplify switching between ability to use DisplayLink devices and ability to use nvidia gpu on optimus laptops. The problem is that they cannot work together.

To simplify switching, you just install a special systemd unit to your system and add additional entry in your bootloader.
So when you are booting, you choose needed mode.

I hope this inconvinience will be fixed and you will be able to use these modes simultaniously.

## Installation

For ArchLinux just install [dl-switch](https://aur.archlinux.org/packages/dl-switch/) from AUR and go to step 3.

For other Linux that use systemd, follow these steps (or ask maintainers of your distribution to include package to repository):
1. Copy file displaylink-workaround1 to /usr/share/X11/xorg.conf.d/
2. Copy displaylink.target and dl-switch.service to /usr/lib/systemd/system/
3. Add additional entry in your bootloader config with kernel option to activate displaylink.target. For rEFInd it looks like this:
    ```
    submenuentry "Boot with DisplayLink workaround" {
        add_options "systemd.unit=displaylink.target"
    }
    ```

## Usage

When you need usual environment with working optimus, just boot as normal.
When you need use several monitors with displaylink device, boot your pc and choose special entry in bootloader.

## Licence

This project is licensed under the terms of the [GPL](http://www.gnu.org/licenses/gpl.html) license.
