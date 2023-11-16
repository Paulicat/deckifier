<p align="center">
 
[//]: <> (site para ícones: https://shields.io/ )
 
<img alt="Maintained" src="https://img.shields.io/badge/Maintained%3F-Yes-green">
<img alt="GitHub last commit" src="https://img.shields.io/github/last-commit/lostalejandro/deckifier">
<img alt="GitHub repo size" src="https://img.shields.io/github/repo-size/lostalejandro/deckifier">
<img alt="Bitbucket open issues" src="https://img.shields.io/bitbucket/issues/lostalejandro/deckifier">
<img alt="GitHub commit activity (branch)" src="https://img.shields.io/github/commit-activity/y/lostalejandro/deckifier">

<hr>

# Deck-ifier

***SteamOS session on any Arch-based distro!***

This repository aims to add required SteamDeck's binaries for Gamescope Wayland session with full "Switch to Desktop", "Game Mode" support and other required components to Arch Linux.

This adds almost all of the required SteamOS dependencies, as well as FPS limiting, flyouts, performance overlay and so on.

<hr>

# IMPORTANT
This only works for ArchLinux running Cinnamon DE and LightDM as display manager. The files named as ```jupiter-biosupdate``` and ```steamos-update``` are just dummy files for Gamescope Session to work. I'm working on an automated installation script but just wanted to share this as soon as i got it working.

<hr>

# Pre-requisites
Before installing, make sure the `multilib` repository is enabled in /etc/pacman.conf and `nano`, `mangohud` and `lib32-mangohud` installed.

# Steps:
## 1. Add needed sudo privileges
```
echo "deck ALL=(ALL) NOPASSWD: /usr/bin/dmidecode -t 11" > /etc/sudoers.d/steam
echo "deck ALL=(ALL) NOPASSWD: /usr/bin/gamescope-session-use-lightdm" > /etc/sudoers.d/gamescope
```

## 2. Cloning this repo and copy files with proper permissions
```
git clone https://github.com/Paulicat/deckifier.git && cd deckifier
```
```
cp -rf rootfs/usr/* /usr
cp -rf rootfs/etc/* /etc
chmod 777 /usr/bin/jupiter-biosupdate
chmod 777 /usr/bin/steamos-update
chmod 777 /usr/bin/steamos-session-select
sudo -u deck -g deck dbus-launch gio set /usr/share/applications/org.valve.gamescope.desktop metadata::trusted true 
chmod a+x /usr/share/applications/org.valve.gamescope.desktop
```

## 3. Reboot and enjoy SteamOS on ArchLinux!
```
reboot
```

# Credits:

To [Joaquín Ignacio Aramendía](https://github.com/Samsagax) and [ChimeraOS](https://github.com/ChimeraOS)'s Team.
To [Adam Jafarov](https://github.com/theVakhovskeIsTaken).
To Gamescope, Valve and Steam developers.
To everyone involved on these amazing projects.
