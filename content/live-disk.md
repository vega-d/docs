---
title: Live Disk Creation (Other Operating Systems)
description: >
  Create and use bootable media on other operating systems.
keywords:
  - Pop_OS!
  - USB
  - Live disk
  - Restore
  - Reinstall
  - Installation
  - System76
  - Verify
  - Checksums

facebookImage: /_social/article
twitterImage: /_social/article

hidden: false
section: hardware-troubleshooting
tableOfContents: true
---

## Overview

Pop!_OS and Ubuntu are remarkably flexible. You can run a full version of Pop!_OS or Ubuntu from a USB drive (often known as a thumb drive, flash drive, or USB stick) in what's known as a *live environment*. Using a live environment (live disk) is useful for:

- [Installing Pop!_OS](/articles/install-pop/)
- [Installing Ubuntu](/articles/install-ubuntu/)
- Recovering your existing operating system
- Backing up files when you can't boot
- [Determining if an issue is caused by hardware or software](/articles/hardware-failure/)
- [Fixing the boot loader](/articles/bootloader)

A live disk is a handy tool to have around!

## Downloading the ISO

In order to install Pop!_OS or Ubuntu, you must first download the .iso image. This is a disk image with the operating system and installer on it. You can [download Pop!_OS here](https://pop.system76.com) or [Ubuntu 20.04 here](https://ubuntu.com/download/desktop/thank-you?version=20.04.2.0&architecture=amd64).

## Verifying the Download

Verifying your download is an important step: we generate a "checksum" for Pop!_OS images and recommend that you verify that your download matches that checksum before trying to install. This ensures that you've received the full, complete download and that it is not corrupted.

### For Ubuntu/Pop!_OS

Assuming you downloaded Pop!_OS to your ~/Downloads folder, open the Terminal (<kbd><font-awesome-icon :icon="['fab', 'pop-os']"></font-awesome-icon></kbd> + <kbd>T</kbd> on Pop!_OS or <kbd>Ctrl</kbd> + <kbd>Alt</kbd> + <kbd>T</kbd> on Ubuntu) and run the following command:

#### For Intel/AMD iso

```
sha256sum Downloads/pop-os_21.04_amd64_intel_7.iso
```

#### For NVIDIA iso

```
sha256sum Downloads/pop-os_21.04_amd64_nvidia_7.iso
```

**Note:** The .iso filenames will change over time, so please make sure you are using the correct .iso filename.

If the checksum does not match the one on the [download page](https://pop.system76.com), you may need to re-download your copy of Pop!_OS and ensure it completes downloading before re-verifying it.

### For Windows

Assuming you downloaded Pop!_OS to your Downloads folder, open the Command Prompt and run the following command:

#### For Intel/AMD iso

```
CertUtil -hashfile Downloads\pop-os_21.04_amd64_intel_7.iso sha256
```

#### For NVIDIA iso

```
CertUtil -hashfile Downloads\pop-os_21.04_amd64_nvidia_7.iso sha256
```

**Note:** The .iso filenames will change over time, so please make sure you are using the correct .iso filename.

If the checksum does not match the one on the [download page](https://pop.system76.com), you may need to re-download your copy of Pop!_OS and ensure it completes downloading before re-verifying it.

## Making the Bootable Drive

In order to make the bootable live disk, you must have a flash drive and software to write the Pop!_OS .iso image to the drive. There's a variety of applications you can use to write disk images to a flash drive, but for this tutorial, we'll use the Disks applicaton for Ubuntu and Etcher for Windows/macOS.

### For Ubuntu/Pop!_OS

Press the <kbd><font-awesome-icon :icon="['fab', 'pop-os']"></font-awesome-icon></kbd>/<kbd><font-awesome-icon :icon="['fab', 'ubuntu']"></font-awesome-icon></kbd> key then type 'disks' to launch the Disks application.

![Disks](/images/live-disk/disks.png)

 Next select the flash drive in the list on left and click on the three dots on the top right of the window. Now select `Restore Disk Image...` and select the Ubuntu or Pop_OS ISO file. Finally, click the `Start Restoring...` button and enter your user password.

![Disks](/images/live-disk/disks-selection.png)

### For Windows/macOS

Etcher is an open source app for Windows and macOS that allows you to "burn images to SD cards & USB drives safely and easily." You can download it at [Etcher.io](https://etcher.io).

Once you have installed Etcher and downloaded the Pop!_OS.iso image, open up the Etcher application. You should see something like this:

![Etcher](/images/live-disk/etcher.png)

Choose `Select Image` and navigate to where you downloaded Pop!_OS, click on it and hit the `Open` button:

![Select Pop!_OS iso](/images/live-disk/open-pop-iso-etcher.png)

Next, select the drive that you want to use. If there is only one, it should automatically recognize that you have a flash drive inserted and select it.

![Etcher Flash Drive Selected](/images/live-disk/etcher-flash-selected.png)

Now hit the `Flash` button and watch the magic happen!

![Flashing Pop!_OS...](/images/live-disk/flashing-pop-os.png)

![Flash Complete](/images/live-disk/flash-complete.png)

Once the flash is complete (it should look like the screenshot above), it's time to boot it up on the machine that you want to install Pop!_OS on!

## Booting From the Live Disk

After creating the live disk, insert the USB drive into your computer, then reboot or power on your system. You'll need to tell the computer to boot from the live disk by holding a key right as you power on:

 Firmware             | Laptops                                                               | Desktops                                              |
 -------------------- | --------------------------------------------------------------------- | ----------------------------------------------------- |
 Proprietary Firmware | Hold <kbd>F7</kbd>/<kbd>F1</kbd>/<kbd>F2</kbd> | Hold <kbd>F12</kbd>, <kbd>F8</kbd>, or <kbd>F10</kbd>                        |
 Open Firmware        | Hold <kbd>Esc</kbd>                                                   |                                                       |

If done correctly, you should see a boot device selection menu, like one of the following images.

![Boot Menu](/images/live-disk/boot-menu.jpg)

Use the arrow keys to select the USB drive, then press <kbd>Enter</kbd> to boot the selection.

Pop!_OS will boot into the familiar Pop!_OS desktop.

![Live Disk](/images/live-disk/live-desktop.png)

## Using the Live Environment

The list provided at the beginning of the article provides links to other articles on using the live environment for hardware testing, restoration/upgrades, and boot repair.

### Repairing an Existing Operating System

Since the live environment is a full Pop!_OS installation, it works just like the normal environment. There are tools and methods that allow to `chroot` (change root) into the normal installation and work in the existing operating system to repair a broken package or other problem that is preventing normal booting.

### Backing Up Files

Perhaps you're reinstalling, or maybe you can't boot but you want to try and recover and back up your files? The live environment will automatically detect and mount most file systems including Linux and Windows. You can then copy files from the disk to another external disk using the familiar <u>Files</u> utility.
