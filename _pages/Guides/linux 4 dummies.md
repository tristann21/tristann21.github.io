---
title: "Linux 4 Dummies"
tags:
    - Guide
    - Linux
date: "2024-07-04"
thumbnail: "https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fwww.extremetech.com%2Fwp-content%2Fuploads%2F2012%2F05%2FLinux-logo-without-version-number-banner-sized.jpg&f=1&nofb=1&ipt=c92203291e35eeeebf3f5ffbd35243eb0ad261013ede709132029fedfa4eeee6&ipo=images"
bookmark: true
---

This is a brief guide for selecting the correct Linux distribution for you. It will also briefly teach you small important details, and show you cool Linux apps you might benifit from!



# Things You Should Know
***

## Figure Out How You Use Your Computer

First, you need to figure out the primary use of your computer. Is it for gaming, office/productive work, web browsing, checking emails, or perhaps a combination of these?

Understanding how you utilize your computer and the roles it fulfills for you is *crucial* in selecting the appropriate Linux distribution for you.

## Avoid Corporate Linux Distributions

Distributions like Ubuntu and Redhat are inherently evil profit incentivized corporations which should be avoided, as they put their business first and user's last much like Microsoft.

Linux distributions made by a community, rather than a corporation, are always the better of choices.

Another important thing to note, there are community [forks](https://pcof.fi/z3md9) of these distributions such as [Linux Mint](https://www.linuxmint.com/), which are based off of Ubuntu. This doesn't mean that Linux Mint is bad, as it only uses Ubuntu as a base and has become it's own thing entirely. And, despite being based off of Ubuntu, Linux Mint is community driven!

## Installing Applications From The Web is Kinda Dumb

![](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fcarlschwan.eu%2F2021%2F05%2F18%2Flas-2021-and-improvements-in-the-applications-infrastructure%2Fdiscover.png&f=1&nofb=1&ipt=9ea2df864982099ddb549c7fdf2c90ee122b5b7796c6b563b8055e5501ae08c7&ipo=images)

Most Linux distributions ship with a software center of some sorts, like the Google Play Store or Apple App Store. Whenever you want to install an application, you almost *never* have to search the web for a binary file and run an installer. *Always* use the app store your distribution ships with.

## Sudo, What is it?

`sudo` is an application which lets your user run a command as a "superuser". Or, to put it simplier, with root privileges. `sudo` = "superuser do"

(yes yes I know sudo has changed a lot since then but to keep this simple that's MY definition of "sudo")

When someone or something online is telling you to execute a script or copy and paste something into the terminal, **make sure you trust** whoever is telling you to do so. And even more so if it requires root privileges.

Another important thing to note; if you see a command on the internet that starts with "$", that's a Linux command. Copy it and get rid of the dollar sign for it to work.

## For Gaming or Professional Use, Avoid "Slow" Distributions

If you're running a gaming rig or use your computer for professional work such as heavy modeling, editing, animating, and whatever else you professionals do; You'll want a more up-to-date Linux distribution.

Distributions such as Linux Mint use something called "LTS Releases". LTS = Long Term Support version. This means that the OS itself and the drivers they're using are very old, and don't get feature updates regularly like other Linux distributions. Rather, they only get security updates and bug fixes, with feature updates only being shipped at a fixed schedule every few years.  The benefit of this is having a super tried and true OS that's reliable, has almost zero bugs, and is very, very secure. But if you need the latest and greatest, this isn't a good option to take. People who use their hardware for professional tasks or for gaming will want a more up-to-date system to keep up with the constant software changes and improvements that get shipped for their machine.

## Automatic Updates Aren't Usually a Thing

Now I'm not saying update everyday. But, it is a good idea to update once every few months.

## Appimages, Snaps, Flatpaks, Debs, RPM's, Binaries, Galore!

Linux isn't really an operating system, it's a kernel. So there are a *ton* of operating systems which run off of the kernel that use their own package formats.

I'll run by these very briefly for ya:

[Appimages](https://appimage.org/) are portable, single binary executables that you can run anywhere on any Linux distribution. I personally recommend [Gear Lever](https://github.com/mijorus/gearlever) which helps you manage Appimages with ease.

[Snaps](https://snapcraft.io/) should be avoided. Same with distributions that depend on them, such as Ubuntu. As for the politics behind it, that is beyond the scope of this guide.

[Flatpaks](https://www.flatpak.org/) are the standard when it comes to Linux applications and work on every distribution, and usually is the primary way of installing apps directly from the developer. These should be the preferred way of installing applications over other formats such as .deb unless you have a reason not to.

Debian binaries (.deb) are Debian installers for applications, as well as Ubuntu and their derivatives. I personally recommend [GDebi](https://launchpad.net/gdebi) to easily install Debian binaries.

`$ sudo apt install gdebi -y`

RPM's are binaries for distributions such as Redhat, Fedora, and openSUSE.

# Linux Distributions
***

## Best for Pretty Much Everybody

![](https://fedoraproject.org/assets/images/atomic-desktops/kde-desktop.jpg)
[Fedora Kinoite](https://fedoraproject.org/atomic-desktops/kinoite/) is great for pretty much every user out there. It is a stable, simple, up-to-date, very secure Linux distribution which utilizes modern Linux technologies such as Wayland, SELinux, OSTree, butterfs, and more!

* Stable, Secure, Modern
* Up-to-date drivers
* BTRFS
* KDE Desktop, makes coming from Windows easier

Fedora Kinoite is a special kind of distribution because it's a "immutable Linux distribution", meaning the operating system, is read-only at its core. This means you can't modify the OS, like the file system, directories, applications, or configuration.

I know what you're probably thinking, "that sounds really limiting!" well, it's not! All your files are in a "home" directory. This is separate from the OS, and where all of your files, settings, and local configurations stay. The applications you install are also sandboxed within your home directory! It's stupidly reliable and secure. And, if anything goes wrong, you can simply rollback to the previous version before you updated. Because, immutable distributions use "snapshots" which you can rollback too at anytime.

Personally I think it is one of the coolest and most fascinating pieces of Linux technology! But, I want to keep this guide simple. So if you want to dig a little deeper into how immutable distributions work, you can read [this amazing article here](https://www.zdnet.com/article/what-is-immutable-linux-heres-why-youd-run-an-immutable-linux-distro/).

## Best for Your Grandma

![](https://www.linuxmint.com/pictures/screenshots/faye/cinnamon.png)
[Linux Mint Debian Edition](https://www.linuxmint.com/download_lmde.php) is for the regular user who do simple tasks and just want their computer to work. My grandma loves this OS!

* Stable, Secure, Tested
* Long Term Support OS
* User Experience is Priority
* Easy Installation for Nvidia Drivers
* Stupidly Simple
* Cinnamon desktop, makes coming from Windows easier


Pro tip; You should setup [Timeshift](https://itsfoss.com/backup-restore-linux-timeshift/), which is preinstalled by default. Timeshift is like Windows restore points. It's best to just select "Weekly" and nothing else for snapshot levels.

A "regular user" in my book is someone who just wants to do simple web browsing, listen to music, edit documents, print stuff, and maybe some video conferencing. Someone who doesn't really care about "having the latest and greatest". Someone who doesn't want anything fancy, just for their machine to work.

If you fit into that category, the best option will always be [Linux Mint Debian Edition](https://www.linuxmint.com/download_lmde.php).

It's one of the easiest to use and most stable distributions out there. It uses tested, tried and true Linux technologies. Linux Mint has always focused on putting the user experience first when it comes to their desktop and their applications with its desktop environment.

## Best for Your Gaming Rig

![](https://bazzite.gg/wp-content/uploads/2024/02/kde.webp)
[Bazzite](https://bazzite.gg/) is thee distribution you *want* if your primary use case is gaming. Built on-top of Fedora Kinoite.

* Games Just Work
* Stable, Secure, Modern
* Performance Enhancements
* Easy to Configure
* Easy Installation for Nvidia Drivers
* Smart Background Updates
* KDE Desktop, makes coming from Windows easier

Bazzite is one of the coolest distributions out there, made by my favorite people at [universal blue](https://universal-blue.org/). It's basically Fedora Kinoite, but built by people who game on Linux every day using this OS. This is the best experience you will have when it comes to PC Gaming, period. If you're curious, you can read all of the cool features and performance improvements they've added [here](https://github.com/ublue-os/bazzite?tab=readme-ov-file#about--features).

However, I highly suggest checking out [protondb](https://www.protondb.com/) before switching over to Linux for gaming. This is a tool that lets you sign into your steam account, and check what games work and don't work on Linux.

Sadly, even though Linux can run games better than on Windows, companies who implement anti-cheats into their multiplayer games will purposefully kick you out if they detect you're not on Windows. So it's best to check protondb before making the jump.

## Best for The Tinkerers

![](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fwww.opensourcefeed.org%2Fassets%2Fimages%2Fpreview%2Fendeavouros-preview.jpg&f=1&nofb=1&ipt=78666aba5bd4ded4a782fe16a7a84dffec2e424480ca4ddc9ab01311500524f6&ipo=images)
[EndeavourOS](https://endeavouros.com/) is thee distribution you'd want to go for if you want true freedom, and to customize anything and everything *exactly* how you want it.

EndeavourOS is based off of Arch, and gives you complete freedom to do whatever you want on your system. **There are no guardrails.**

* Easy to Configure
* Easy Installation for Nvidia Drivers
* Huge Repository
* Complete Freedom

Some see this as a great thing, others don't. With EndeavourOS, it is *your* responsibility to setup the security, to setup your desktop environment, your packages, drivers, everything. Because of this, EndeavourOS is a very terminal centric distribution, made for people who either know what they're doing or want to learn and don't mind spending hours of troubleshooting and setting up their system how they want it.

You are responsible for everything. If something breaks, it is up to you to fix it. EndeavourOS is only as stable as you make it to be.

# How do I Install Linux?
***

Congrats on picking your Linux distribution! This guide assumes you're using Windows.

## Testing Linux before installing it

You can format Linux onto a thumb drive and boot off of said thumb drive without affecting your Windows installation at all! It won't touch your computer's drive either. *Some* Linux distributions will boot you into a test environment where you can do whatever you want, and see how comfortable you are in Linux! If however you're using a Linux distribution that doesn't have a live test environment, you can always look up on YouTube about the distribution you're thinking of using!

<iframe width="560" height="315"
src="https://www.youtube-nocookie.com/embed/Zdn-sgKT0c8"
frameborder="0"
allow="autoplay; encrypted-media; picture-in-picture"
allowfullscreen></iframe>

## Prerequisites

1. You need a thumb drive that has at least 8 gigabytes of storage
1. You must make sure you have nothing important on the thumb drive, as it will be reformatted to be a bootable Linux drive. (You can revert it back later) First, you need a thumb drive that doesn't have any important files on them
1. If you have anything important on your computer that you don't want to lose, back them up ***before*** installing Linux; As installing Linux will reformat your computer's drive as well.

## Making a Bootable Thumb Drive

<iframe width="560" height="315"
src="https://www.youtube-nocookie.com/embed/GvI0oyTsuxI"
frameborder="0"
allow="autoplay; encrypted-media; picture-in-picture"
allowfullscreen></iframe>

1. Download whatever Linux distribution you want to use
1. Download [Rufus](https://rufus.ie/en/)
1. Plugin your thumb drive
1. Launch Rufus
1. Select the thumb drive you wish to format Linux onto
![](/assets/img/thumbnail/rufus1.png)
1. Press "Select" in Rufus to open file manager
![](/assets/img/thumbnail/rufus2.png)
1. Click on the ISO file, then press "Open"
![](/assets/img/thumbnail/rufus3.png)
1. Click on "Start"
![](/assets/img/thumbnail/rufus4.png)
1. Ensure "Write in ISO mode" is selected, and then click "OK"
![](/assets/img/thumbnail/rufus5.png)

Now Windows *might* come up and saying it can't read your thumb drive, or that it's corrupted; **Do not press "OK"** Just close out of the pop up. That's just Windows being stupid and trying to get rid of your Linux!

Next, you need to look up how to enter into the "one time boot menu" screen on your computer.

* If you built your computer yourself, search on duckduckgo "How to boot into one time boot menu with (motherboard manufacturer)" e.g., acer, msi, asus.
* If you bought a prebuilt computer, search on duckduckgo "How to boot into one time boot menu with (computer manufacturer)" e.g., dell, lenovo, hp.
* If you bought a laptop, search on duckduckgo "How to boot into one time boot menu with (laptop manufacturer)" e.g., dell, lenovo, hp.

Now that you have figured out which key you need to press in order to access the boot menu, shutdown your computer, press and hold down on the key, and then turn it back on. Don't let go until you see the one time boot menu pop up.

It'll look something like this;

![](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fi1.wp.com%2Fdellwindowsreinstallationguide.com%2Fwp-content%2Fuploads%2F2016%2F07%2Fboot-menu-one-time-usb2.png%3Fssl%3D1&f=1&nofb=1&ipt=3791dfacf393fbe0cbdaed1835e3d5097d9fd047f8f6ec1e4375a7ecaef12e34&ipo=images)

It will either be named what your thumb drive is named, e.g., sandisk. Or, it will be named whatever Linux distribution you formatted onto it.

Use the up and down arrow keys to select your thumb drive, then press the Enter when you select it.

![](https://forum.zorin.com/uploads/default/original/2X/2/2c655f9b53b921a9022bbaa87b072472442a04e7.jpeg)

If for whatever reason the "Perform MDK management" screen pops up, it means your computer has something called "Secure Boot" on and won't let you boot into Linux. Secure Boot is made primarily for Windows, and needs to be disabled in order to continue.

Look up your laptop/computer/motherboard manufacturer on how to disable Secure Boot.


# Cool Software You Should Know
***

I want to quickly go over some cool pieces of software I feel like you'd find useful!

**Remember to install them via your distributions app store!**

## GPU Screen Recorder

[https://flathub.org/apps/com.dec05eba.gpu_screen_recorder](https://flathub.org/apps/com.dec05eba.gpu_screen_recorder)

The fastest screen recorder for Linux. It lets you record, livestream, and take clips all in a very, very simple user interface that takes seconds to setup.

## Lutris

[https://flathub.org/apps/net.lutris.Lutris](https://flathub.org/apps/net.lutris.Lutris)

Easily install and setup launchers from Epic Games, GOG, itch.io, EA, Ubisoft Connect, and more!

## Heoric Games launchers

[https://flathub.org/apps/com.heroicgameslauncher.hgl](https://flathub.org/apps/com.heroicgameslauncher.hgl)

A Native Linux games launcher for installing Epic Games, Amazon Prime, and GOG games all in one launcher. The best way to install and manage games from those services, in my opinion!

## Spot

[https://flathub.org/apps/dev.alextren.Spot](https://flathub.org/apps/dev.alextren.Spot)

Stupidly fast and simple Spotify music streaming client for Spotify Premium users.

## Deja Dup Backups

[https://flathub.org/apps/org.gnome.DejaDup](https://flathub.org/apps/org.gnome.DejaDup)

Securely backup your home directory locally, remotely, or via the cloud with services such as Google Drive. Supports encrypting your backups!

## Vesktop

[https://flathub.org/apps/dev.vencord.Vesktop](https://flathub.org/apps/dev.vencord.Vesktop)

Vesktop is *thee* best Discord client for Linux. It's native, fast, and let's you screenshare on Linux!

## Prism Launcher

[https://flathub.org/apps/org.prismlauncher.PrismLauncher](https://flathub.org/apps/org.prismlauncher.PrismLauncher)

The best Minecraft launcher when it comes to managing modpacks and multiple installations. It lets you download modpacks straight from curseforge and Modrinth!

## Flameshot

[https://flathub.org/apps/org.flameshot.Flameshot](https://flathub.org/apps/org.flameshot.Flameshot)

A Free and Open Source alternative to LightShot! If you wan't to rebind your print screen key with flameshot, go into your keyboard shortcut settings and make a new custom shortcut. Set printscreen to `flatpak run org.flameshot.Flameshot gui`






# I hope this post finds you well. Please take care of yourself.

![](/assets/img/thumbnail/IMG_20240629_084357441_1.jpg)
