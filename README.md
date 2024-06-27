---
title: README
author: Christian Külker
version: 0.1.0
date: 2024-06-07

---

# Apple Bluetooth Keyboard

This document describes how to set default values on Bluetooth bind for the
Apple Bluetooth Keyboard, such as disabling the `fnmode` to address certain key
mapping issues.

## Issue Description

On recent Debian operating systems, like Debian 12 Bookworm, the Apple
Bluetooth Keyboard generally connects without issue. However, certain keys
(e.g., 'j', 'k', 'l') may function as a number pad instead of producing letter
characters, akin to having __Num Lock__ activated.

### Resolution

Disabling `fnmode` by setting it to 0 resolves this key behavior anomaly.

Other solutions are available on the Arch Linux wiki at [Apple Keyboard on
ArchWiki](https://wiki.archlinux.org/title/Apple_Keyboard). However, this
solution primarily pertain to the MATE desktop environment on Debian, where the
standard intramfs setup requires no modifications.

### Why this Method?

This approach avoids the use of `modprobe` and offers a simple, immediately
reversible solution if changes need to be adjusted dynamically.

# Installation

## Method 1: Direct Installation via Git

```bash
# As root
mkdir -p /opt/apple-bluetooth-keyboard
chown $USER:$GROUP /opt/apple-bluetooth-keyboard
# As $USER
cd /opt
git clone https://github.com/ckuelker/apple-bluetooth-keyboard.git
# As root
cd /opt/apple-bluetooth-keyboard/etc/udev/rules.d/
cp 90-apple-bluetooth-keyboard.rules /etc/udev/rules.d/
udevadm control --reload-rules
```

## Method 2: Using Ansible

Utilize the Ansible role available at
<https://github.com/ckuelker/ansible-role-apple-bluetooth-keyboard> to install
and activate the `udev` rule.

