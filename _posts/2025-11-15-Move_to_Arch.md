---
layout: post
title: Move to Arch
date: 2025-10-31
name: Simon Gray
tags:
  - learning
update: 2026-02-22
---

# The Move to Arch
I've been a lifetime user of windows, however for my job I've been using Linux where I can, but in my current role there isn't an option for this, but I've been actively enjoying my homelab for a few years now and plan to continue using it for many years in the future.

While windows is really popular and works well, I don't like the direction that it's going, but the three main issues for me are really the following:
1. AI getting shoved down your throat
2. The deployment of recall and just the bloatware which is all though the system
3. Learning with Omarchy
For these reasons I wanted to start looking at other operating systems, and Arch just seems like the logical option, I didn't want to use something which was already made by someone else, so while Omarchy was cool to use, and a good template I didn't want to use it long term. Just trusting someone else's configuration doesn't sit well with me, and because I've got the skill set to actually do it, while looking at configuring it the main reason that I didn't want to switch was because of the issue with gaming, but now that steam is getting so good, and the compatibility for all the games I want to play is at a good level I think it'd time to make the switch.


## Omarchy Issues
Just adding on this the updates have caused a ton of issues with the boot drive, and I don't know what's caused it because I just downloaded and installed it without actually understanding what was going on...

# Transition Issues
The main issues with it so far have been ensuring all the correct drivers are installed and compatible with each other, there are some things which just don't really work well, for example getting jellyfin to work is just painful.

# Guides

## Installing Stuff

Steam
Uncomment multilib /etc/pacman.conf
```
[multilib]
Include = /etc/pacman.d/mirrorlist
```

```
sudo pacman -S flatpak
flatpak install flathub com.bambulab.BambuStudio
flatpak run com.bambulab.BambuStudio
```

## DHCP
So it turns out there's multiple things which can provide DHCP, and I've had three of them running which causes the gain an loss of IP addresses with general instability
```
systemctl --type=service | grep -Ei 'network|dhcp|wpa|iwd|conn'
sudo ip link set <ID> down
```

## Physical Networking
```
sudo vim /etc/systemd/network/30-thunderbolt-dock.network
sudo vim /etc/systemd/network/20-
sudo dhclent <inet ID>
```

## Lenovo Dock
To get a dock to work you need to download bolt
```
sudo pacman -S bolt
sudo systemctl enable --now bolt.service
boltctl
sudo boltctl authorize <UUID>
sudo boltctl enroll <UUID>
```

## Power Checking
```
upower -e
upower -i <ID>
```

## New Tools

### fzf
This is a pretty cool function that I'm starting to use more and more, for things like opening a pdf and just looking for files to edit, but there's still so much more
```
zathura $(fzf)
nvim | $(fzf)
```

### zathura
This is now my pdf viewer, it's really quick and doesn't have al lthe bloat that others have (I'm looking at you adobe)

### rg
Still figuring this one out, but I've used
```
find . -type f | xargs grep <REGEX>
```
so being able to just use the following if pretty handy
```
rg -i <REGEX>
```
