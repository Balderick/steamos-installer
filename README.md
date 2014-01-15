# steamos-installer

Ye Olde SteamOSe - a modified SteamOS installer, with support for older and virtualized computers

The future is here, but it's a bit new isn't it?
SteamOS is now shipping, in beta form at least, and it's all cool and stuff.

But what about those of us without a modern, UEFI-based computer spare?

Ye Olde SteamOSe is for you.

# Improvements

- SteamOS requires UEFI. Ye Olde SteamOSe works with UEFI or BIOS.
- SteamOS requires a 2GB USB Stick to install. Ye Olde SteamOSe works from a DVD or a 1GB USB Stick.
- SteamOS requires a real computer. Ye Olde SteamOSe has 3D acceleration on VMWare and Virtualbox, out of the box.
- SteamOS says it needs 500GB of disk space, but that's a lie. Ye Olde SteamOSe requires the same amount of space as SteamOS really does - 40.5GB minimum (of that 10GB and any more available is for games).
- SteamOS takes over your PC. Ye Olde SteamOSe supports dual-boot.
- SteamOS only supports Realtek networking, or firmware-free networking. Ye Olde SteamOSe supports everything a modern Linux does, including WiFi.
- SteamOS monopolizes drives. Ye Olde SteamOSe can resize NTFS partitions.
- SteamOS only outputs to HDMI audio. Ye Olde SteamOSe supports almost any sound card with a couple of clicks.
- SteamOS only supports basic partitions. Ye Olde SteamOSe supports LVM and software RAID.

![SteamOS on VMware](http://i.imgur.com/a3jnZ6r.png)

# Planned improvements

- Clean up audio support to remove unmute step.

# How to install?

A DVD image is always available via BitTorrent at http://directhex.github.io/steamos-installer/

To get started, download the torrent.

Otherwise, clone this repo, and run `./gen.sh`.

## Installing from a DVD

Just burn the ISO to a blank DVD from your favourite tool, and boot it.

## Installing from USB (Mac)

Open a Terminal window from the Utilities section of Applications.

Type `diskutil list` to get a list of devices - one of them will be your USB stick (e.g. `/dev/disk2`). Follow the Linux instructions below, with this `/dev/diskX` entry instead of `/dev/sdX`

## Installing from USB (Linux)

Plug in the USB stick and run `dmesg`; look for a line similar to this:

    [377039.485179] sd 7:0:0:0: [sdc] Attached SCSI removable disk

In this case, `sdc` is the device name for the USB stick you just inserted. Now we put the installer on the stick, as root (e.g. use `sudo`) run 

    dd bs=1M if=/path/to/yeolde.iso of=/dev/sdX 
    
sdX should be the USB stick device from the information you received from `dmesg`. Be sure to use sdX, not sdX1 or sdX2. Then boot into the stick.

## Installing from USB (Windows)

Download [Win32 Disk Imager](http://sourceforge.net/projects/win32diskimager/) and use it to copy the .iso to your USB stick (1GB minimum size).

## Once the installer is up...

Pick the "Automatic Install" option to wipe the first hard disk in your system and install SteamOS to it.

For more sophisticated booting - e.g. dual-boot or custom partition sizes - select the "Expert" or "Power User" options - thse are documented on the Wiki.

Beyond that, just follow [Valve's instructions from their site](http://store.steampowered.com/steamos/buildyourown), steps 7 onwards under "Custom Installation" - Ye Olde SteamOSe should behave exactly like the real SteamOS, except it works on more systems.

## Updating

Before you generate a new image you need to ensure that your pull is up to date as things change quickly:

- `git pull` in the steamos-installer directory will ensure you have the latest code.
- `./gen.sh -d` will ensure that you download the latest SteamInstaller.zip

# Known issues and workarounds

- 3D support is broken in Big Picture Mode itself and in 32-bit games in VirtualBox. This is a flaw in the Debian packaging of the VirtualBox guest drivers.
- Sound card selection, volume levels, etc, must be set with pavucontrol, not the GNOME volume slider.

# How can I help?

Test it and report back to #steamos on Freenode

Or support me by donating - Donate via [PayPal](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=888397), [Steam](http://steamcommunity.com/id/directhex/wishlist), or [Amazon](http://www.amazon.co.uk/wishlist/LN9AGFCAGAHR). Donations will be used to help with testing - wifi adapters, hard disks, graphics cards, etc.

# Special Thanks

- Michael Waltz (ecliptik) for his continued contributions.
- Anonymized benefactors for their sponsorship (~400 day VMware key; £30; 1 month reddit Gold; Shoot Many Robots game).
- Various Valve engineers for their help.
