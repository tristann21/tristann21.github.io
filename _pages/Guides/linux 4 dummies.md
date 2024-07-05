---
title: "Linux 4 Dummies"
tags:
    - Guide
    - Linux
date: "2024-07-04"
thumbnail: "https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fwww.extremetech.com%2Fwp-content%2Fuploads%2F2012%2F05%2FLinux-logo-without-version-number-banner-sized.jpg&f=1&nofb=1&ipt=c92203291e35eeeebf3f5ffbd35243eb0ad261013ede709132029fedfa4eeee6&ipo=images"
bookmark: true
---

This is a brief guide for selecting the correct Linux distribution for you. It will also cover file systems, Linux applications, and file formats, along with useful tips and tricks for your Linux distribution, and more!


# Things You Should Know
***

## Avoid Corporate Linux Distributions

Distributions like Ubuntu and Redhat are inherently evil profit incentivized corporations which should be avoided, as they put their business first and user's last much like Microsoft.

However, there are community [forks](https://en.wikipedia.org/wiki/Fork_(software_development) of these distributions such as [Linux Mint](https://www.linuxmint.com/), which are based off of Ubuntu. This doesn't mean that Linux Mint is bad, as it only uses Ubuntu as a base and has become it's own thing entirely. Despite being based off of Ubuntu, Linux Mint is community driven.

## Installing Applications From The Web is Kinda Dumb

![](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fcarlschwan.eu%2F2021%2F05%2F18%2Flas-2021-and-improvements-in-the-applications-infrastructure%2Fdiscover.png&f=1&nofb=1&ipt=9ea2df864982099ddb549c7fdf2c90ee122b5b7796c6b563b8055e5501ae08c7&ipo=images)

Most Linux distributions ship with an app store of some sorts, just like your phone does. Whenever you want to install an application, you almost *never* have to search the web for a binary file and run an installer. *Always* use the app store your distribution ships with.

## Sudo, what is it?

`sudo` is an application which lets your user run a command as a "superuser". Or, to put it simplier, with root privileges. `sudo` = "superuser do"

(yes yes I know sudo has changed a lot since then but to keep this simple that's the definition of "sudo")

When someone or something online is telling you to execute a script or copy and paste something into the terminal, **make sure you trust** whoever is telling you to do so. And even more so if it requires root privileges.

Another important thing to note; if you see a command on the internet that starts with "$", that's a Linux command. Copy it and get rid of the dollar sign for it to work.

## Appimages, Snaps, Flatpaks, Debs, RPM's, Binaries, Galore!

Linux isn't really an operating system, it's a kernel. So there are a *ton* of operating systems which run off of the kernel that use their own package formats.

I'll run by these very briefly for ya:

[Appimages](https://appimage.org/) are portable, single binary executables that you can run anywhere on any Linux distribution, anywhere, and they don't require being installed. I personally recommend [Gear Lever](https://github.com/mijorus/gearlever) which helps you manage Appimages with ease.

[Snaps](https://snapcraft.io/) should be avoided, same with distributions that depend on them, such as Ubuntu. As to the politics behind it, is beyond the scope of this guide.

[Flatpaks](https://www.flatpak.org/) are the standard when it comes to Linux applications and work on every distribution, and are the main way of installing apps directly from the developer. These should be the preferred way of installing applications over other formats such as .deb unless you have a reason not to.

Deb files (.deb) are Debian installers for applications, as well as Ubuntu and their derivatives. I personally recommend [GDebi](https://launchpad.net/gdebi) to easily install .deb applications.

`$ sudo apt install gdebi -y`

RPM's are installers for applications for distributions such as Redhat, Fedora, and openSUSE.

## For Gaming or Professional Use, Avoid "Slow" Distributions

If you're running a gaming rig or use your computer for professional work such as heavy modeling, editing, animating, and whatever else you professionals do; You'll want a more up-to-date Linux distribution.

Before immutable distributions, Ubuntu, Debian, Linux Mint, and others use something called "LTS Releases". LTS = Long Term Support version. This means that the OS itself and the drivers they're using are very old, and don't get feature updates regularly like other Linux distributions. Rather, they get feature updates at a fixed schedule every few years, and security updates and bug fixes are the only updated allowed. The benefit of this is having a super tried and true OS that's reliable, has almost zero bugs, and is very, very secure. But if you need the latest and greatest, this isn't a good option to take. {eople who use their hardware for professional tasks or gaming, will want a more up-to-date system to keep up with the constant hardware changes and improvements for their hardware.

## Automatic Updates Aren't Usually a Thing

Now I'm not saying update everyday. But, it is a good idea to update once every few months.

# Getting Started
***

## How Do I Use My Computer?

First, lets figure out the primary use of your computer. Is it for gaming, office/productive work, web browsing, checking emails, or perhaps a combination of these?

Understanding how you utilize your computer and the roles it fulfills for you is *crucial* in selecting the appropriate Linux distribution for you.

## Best for Pretty Much Anybody

![](https://fedoraproject.org/assets/images/atomic-desktops/kde-desktop.jpg)

You can never go wrong with Fedora Kinoite. It is a stable, up-to-date, very secure Linux distribution which utilizes modern Linux technologies such as Wayland, SELinux OSTree, butterfs, and more!

* Stable, Secure, Modern
* Up-to-date drivers
* BTRFS
* Best overall

Fedora Kinoite is a special kind of distribution because it's a "immutable Linux distribution", meaning the operating system, is read-only at its core. This means you can't modify the OS, like the file system, directories, applications, or configuration.

I know what you're probably thinking, "that sounds really limiting!" well, it's not! All your files are in a "home" directory. This is separate from the OS, and where all of your files, settings, and local configurations stay.

Basically, immutable distributions are one of thee most stable, reliable, and secure distributions out there. And, if anything goes wrong, you can simply rollback to the previous version before you updated. As immutable distributions use "snapshots" which you can rollback too at anytime.

Personally I think it is one of the coolest and most fascinating pieces of Linux technology! But, I want to keep this simple. So if you want to dig a little deeper into how immutable distributions work, you can read [this](https://www.zdnet.com/article/what-is-immutable-linux-heres-why-youd-run-an-immutable-linux-distro/) amazing article here.

## Best for Your Grandma

![](https://www.linuxmint.com/pictures/screenshots/faye/cinnamon.png)

Linux Mint is for the regular users who do simple tasks and just want their computer to work.

* Stable, Secure, Tested
* Long Term Support OS
* User Experience is Priority
* Easy Installation for Nvidia Drivers


Pro tip; You should setup [Timeshift](https://itsfoss.com/backup-restore-linux-timeshift/), which is preinstalled by default. Timeshift is like Windows restore points. It's best to just select "Weekly" and nothing else for snapshot levels.

A "regular user" in my book is someone who just wants to do simple web browsing, listen to music, edit documents, print stuff, and video conferencing. Someone who doesn't really care about "having the latest and greatest". Someone who doesn't want something fancy.

If you're just a regular user who fits into that category, the safest option will Always be [Linux Mint](https://www.linuxmint.com/). or what I personally recommend; [Linux Mint Debian Edition](https://www.linuxmint.com/download_lmde.php).

It's one of the easiest to use and most stable distributions out there, that uses tested, tried and true Linux technologies. Linux Mint has always focused on putting the user first when it comes to their desktop and their applications, making every single option have a user interface should you need it.

Linux Mint Debian Edition takes the stability to a step further by instead using Debian as a base, rather than Ubuntu.

## Best for your Gaming Rig

![](https://bazzite.gg/wp-content/uploads/2024/02/kde.webp)

Bazzite is the distribution you *want* if you're primary use case is gaming. Built on-top of Fedora Kinoite.

* Games Just Work
* Stable, Secure, Modern
* Performance Enhancements
* Easy to Configure
* Easy to Install Nvidia Drivers
* Smart Background Updates

Bazzite is one of the coolest distributions out there, made by my favorite people at [universal blue](https://universal-blue.org/). It's basically Fedora Kinoite, but built by people who game on Linux every day, and use this OS. This is the best experience you will have when it comes to PC Gaming, period.

However, I highly suggest checking out [protondb](https://www.protondb.com/) before switching over to Linux for gaming. This is a tool that lets you sign into your steam account, and check what games work on Linux and what games don't.

Sadly, while games not only run on Linux, but even better than on Windows nowadays; Companies who introduce anti-cheats into their multiplayer games will purposefully kick you out if they detect you're not on Windows. So it's best to check before making the jump.

## Best for the Tinkerers

![](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fwww.opensourcefeed.org%2Fassets%2Fimages%2Fpreview%2Fendeavouros-preview.jpg&f=1&nofb=1&ipt=78666aba5bd4ded4a782fe16a7a84dffec2e424480ca4ddc9ab01311500524f6&ipo=images)

EndeavourOS is thee distribution you'd want to go for if you want true freedom, and to customize anything and everything *exactly* how you want it.

EndeavourOS is based off of Arch, and gives you complete freedom to do whatever you want on your system. **There are no guardrails.**

Some see this as a great thing, others don't. With EndeavourOS, it is *your* responsibility to setup the security, to setup your desktop environment, your packages, drivers, everything. Because of this, EndeavourOS is a very terminal centric distribution, made for people who either know what they're doing or want to learn and don't mind spending hours of troubleshooting and setting up their system how they want it.

You are responsible for everything. If something breaks, it is up to you to fix it.

# Cool Software You Should Know
***

Congrats on picking your Linux distribution! 'm gonna go over this section briefly and quickly.

**Remember to install them via your distributions app store!**

## GPU Screen Recorder

https://flathub.org/apps/com.dec05eba.gpu_screen_recorder

The fastest screen recorder for Linux. It lets you record, livestream, and take clips all in a very, very simple user interface that takes seconds to setup.

## Lutris

https://flathub.org/apps/net.lutris.Lutris

Easily install and setup launchers from Epic Games, GOG, itch.io, EA, Ubisoft Connect, and more!

## Heoric Games launchers

https://flathub.org/apps/com.heroicgameslauncher.hgl

A Native Linux games launcher for installing Epic Games, Amazon Prime, and GOG games all in one launcher. The best way to install and manage games from those services, in my opinion!

## Spot

https://flathub.org/apps/dev.alextren.Spot

Stupidly fast and simple Spotify music streaming client for Spotify Premium users.

## Deja Dup Backups

https://flathub.org/apps/org.gnome.DejaDup

Securely backup your home directory locally, remotely, or via the cloud with services such as Google Drive. Supports encrypting your backups!

## Vesktop

https://flathub.org/apps/dev.vencord.Vesktop

Vesktop is *thee* best Discord client for Linux. It's native, fast, and let's you screenshare on Linux!

## Prism Launcher

https://flathub.org/apps/org.prismlauncher.PrismLauncher

The best Minecraft launcher when it comes to managing modpacks and multiple installations. It lets you download modpacks straight from curseforge and Modrinth!

## Flameshot

https://flathub.org/apps/org.flameshot.Flameshot

A Free and Open Source alternative to LightShot! If you wan't to rebind your print screen key with flameshot, go into your keyboard shortcut settings and make a new custom shortcut. Set printscreen to `flatpak run org.flameshot.Flameshot gui`


# Conclusion
***

I hope you found this guide useful, and I hope even more you enjoy Linux! I'm really happy you took the time to read this and learn more about it and make an actual informed decision. Whether you're switching for freedom, security, privacy, performance, battery life, or whatever else, I'm excited to have another penguin on board!


I hope this post finds you well. Please take care of yourself.

![](https://cdn.discordapp.com/attachments/1064006615889612861/1256341921077661848/IMG_4451.png?ex=66885417&is=66870297&hm=e0a81dcbd7f4ba1df4f806c780ea4f16729d1499d758b2812b1a0c91a352ebc3&)
