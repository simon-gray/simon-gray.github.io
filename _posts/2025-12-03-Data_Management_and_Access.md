---
layout: post
title: Data Management and Access
date: 2025-12-03
name: Simon Gray
tags:
  - homelab
update: 2025-12-03
---

# Data Management
The overall data management for my home environment is something that I really want to improve, the goal for my infrastructure is to go towards IaS, this will be done through scripts on GitHub, and then I'll have the bulk storage on my NAS

## Passwords and Security
I strongly believe in [Kerckhoff's principle](https://en.wikipedia.org/wiki/Kerckhoffs%27s_principle), '*Design your system assuming that your opponents know it in detail*', it shouldn't be a secret what you use, as that's how you improve security through that level of transparency.

For my system I'm using multiple things for my management of passwords, personally I want to look at Yubiko for my 2fa in the future, but right now I use Bitwarden, Aegis, Microsoft Authenticator and  Proton Pass, this isn't great but they each have a use, when I did my initial investigation into a password manager Bitwarden what the best option, although that was in 2022, Aegis is for my 2fa tokens, I didn't like Microsoft Authenticator as it's hard to export, but we've got some things which required it in that ecosystem, which is why I still have it. Proton Pass is used because of the email aliases, something which I'm going to be implementing more.

Previously I've used keepass for my local homelab passwords, but it just doesn't go very well with my workflow

## Data Backup Strategy
I've been trying to use the 3-2-1 backup strategy, right now I've got copies on my NAS, Google Cloud, and multiple local copies, everything that's really important to me is in 3 locations, and then stuff that I don't care about are the movies and TV shows, these can just have a single copy, because if I lose it, then I can always just download it again on Usenet.

The item which is still under development is the management of the recovery codes, right now I've got three options, the first is I've got a physical USB with everything stored on it, right now that's unencrypted, which isn't how I'm going to store it long term, but right now that's what I've done to make sure I don't forget the encryption code of it.

# Hit By a Bus
There currently isn't anything planned to give access to my accounts, It's something which I'll work on in the future, however I just don't have it right now.

I also have the concern about for when I travel, and the best way to track this, I've taken a physical piece of cardboard in my wallet which has information that's only I'll understand how it's used to get access to my accounts If I lose my phone, but that probably doesn't help as I'll have lost my wallet as well.
