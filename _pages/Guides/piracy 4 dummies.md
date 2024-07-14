---
title: "Piracy 4 Dummies"
tags:
    - Guides
    - Cool Stuff
date: "2024-07-12"
thumbnail: "https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Flogos-world.net%2Fwp-content%2Fuploads%2F2022%2F06%2FThe-Pirate-Bay-Symbol.png&f=1&nofb=1&ipt=1ea8591a5c760e9fc51ac5d949f800dafb1ba56a6e36bfc4a84a01d369b55979&ipo=images"
bookmark: true
---

This small guide shows you cool applications that can help you torrent media whether for educational or personal use. It'll also show you how do to it anonymously if need be!


# Things you should know
***

## Make sure what you're downloading is legit
If you're downloading an executable, like a game, it can potentially be malicious depending on where you're downloading your files from. It's better to be safe than sorry and do a quick scan with something such as [Virustotal](https://www.virustotal.com/gui/home/upload). Most sources in this guide are considered trustworthy though, so long as you use an adblocker!

## Avoid uTorrent
uTorrent contained a hidden Bitcoin miner a while back. Someone was making a crap ton of money off of everyone running it and also downloaded a bunch of bloatware in the background. Because it's a closed-source program, no one had any idea. It's always best practice to use open-source alternatives to your favorite software if there are any.

## Your ISP might hate you
If you're in the States or in a country where they have anti-piracy laws in place, you *need* to use a VPN or else your ISP can and will shut your internet down. Other countries, however, such as Brazil or China, could care less if you're torrenting Western media.

The best and most trusted VPN you should use is [Mullvad VPN](https://mullvad.net), in conjunction with something such as [qBittorrent](https://www.qbittorrent.org/), which is what we will be using in this guide.

## You don't torrent books
![](https://camo.githubusercontent.com/75a381460ede01844b7fa14f7b4f38af48f51995c1ce26ff42359b076b54e464/68747470733a2f2f646c2e6b6f6f646f7265616465722e636f6d2f73637265656e73686f74732f342e706e67)

The interesting thing about books is that they're such small files because they only contain text and rarely images, so there aren't really ways to torrent them. If you wish to access free information, I suggest [Anna's Archive](https://annas-archive.org). The largest online library to ever exist. 100% free!

Most books online are downloaded as a PDF. However, some of them can be downloaded as a [`.epub`](https://en.wikipedia.org/wiki/EPUB). If so, you will need an [ebook](https://en.wikipedia.org/wiki/Ebook) reader in order to view them. Most of these ebook readers can also view PDF files as well, so you can have all of your ebooks in one place!

I personally suggest Koodoo Reader, which you can download [here](https://github.com/koodo-reader/koodo-reader/releases/tag/v1.6.7).

However, people do torrent online *libraries* rather than individual books to archive them should something happen. So, if you're a cool tech guy who has a few spare terabytes in their home server and want to contribute, you can learn more [here](https://annas-archive.org/datasets)!


## It'd be smart to use an AdBlocker

![](/assets/img/thumbnail/adblock.png)

Whether torrenting media or streaming it, an Adblocker can protect you from malware and also keep you sane while it blocks three thousand pop-ups trying to get you to click something you shouldn't. I personally recommend [uBlock Origin](https://ublockorigin.com/).

# qBittorrent setup (General torrenting)
***
![](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fi.ytimg.com%2Fvi%2Fu7hORAD2O44%2Fmaxresdefault.jpg&f=1&nofb=1&ipt=3a964603e080e6775ce9e8a0898ab056367d9f5fc01171f1deab34e2f135e031&ipo=images)

This is a general setup that lets you torrent and seed whatever type of file/piece of media you want to and doesn't cater to anything specific. First, download and open [qBittorrent](https://www.qbittorrent.org/).

## Binding your VPN's network interface
After that, it's time to connect to our VPN provider and bind qBittorrent to that network interface, ensuring that our IP address won't get leaked while torrenting.

For MacOS, there's a tutorial for you [here](https://www.youtube.com/watch?v=f8QznInFaD4).

For Windows, go to qBittorrent and click "preferences" at the top, on the left scroll down to "advanced", select the drop-down menu named "Network interface", and then click on "Mullvad". After that, click apply, then OK.

After you've done all that, you can check if your IP address is being leaked by using [ipleak.net](https://ipleak.net/), which has a cool "Torrent Address detection" button which will tell you what IP address is showing up whenever you torrent a file! 

# Torrent sources
***
![](https://external-content.duckduckgo.com/iu/?u=https%3A%2F%2Fwww.2-remove-virus.com%2Fwp-content%2Fuploads%2F2020%2F04%2F1337x.png&f=1&nofb=1&ipt=5b9b320af502861ff4cec62221e2303cf5401cbfe0a7fc6c4336841343d48d54&ipo=images)

## Torrent search engines
There are torrent search engines out there such as [1337x](https://1337x.to/), which is basically Google but for torrenting.

## Movies and TV
For specific other kinds of media, such as movies or TV, [watch so much](https://watchsomuch.to/) is a movie and TV torrent search engine.

## Games
For games, while I personally prefer [Hydra Launcher](https://github.com/hydralauncher/hydra), (which is later on in this guide), there are multiple game torrenting sites. My favorite is [FitGirl Repacks](https://fitgirl-repacks.site/), but there are other alternatives such as [DODI Repacks](https://dodi-repacks.site/). DODI can sometimes lead you to websites that require you to turn off your AdBlock, which is why I recommend FitGirl over DODI.

## Music
For music or any other type of media, [1337x](https://1337x.to/) is your best bet.

However, I suggest taking a look at [spotDL](https://github.com/spotDL/spotify-downloader) which is a much easier tool to use for downloading music.

Also, if you're torrenting music and need a local music player, I personally recommend [Strawberry Music Player](https://www.strawberrymusicplayer.org/) for Linux and [Clementine Music Player](https://www.clementine-player.org/) for Windows. While I prefer Strawberry, which is available for Windows and Mac, that requires a $5 subscription. [VLC](https://www.videolan.org/vlc/) is also a great option!

# Torrent software for specific media
***

**Please remember to connect to your VPN if you're in a country that has anti-piracy laws!!**

## Hydra Launcher (Game torrenting)
![](https://raw.githubusercontent.com/hydralauncher/hydra/main/docs/screenshot.png)

The best way to torrent games is with this amazing free and open-source application called [Hydra Launcher](https://github.com/hydralauncher/hydra).

Hydra is a game launcher with a BitTorrent client, a repack scraper (heavily compressed torrents so they can be downloaded quicker and shared more efficiently), and a game downloader built in! No account is required to use it.

When you first download Hydra, you'll notice you're unable to download any games because there aren't any sources available. We have to add them ourselves. Luckily, a community-made website was made just for that! After you have installed Hydra Launcher, you can visit [hydralinks.cloud](https://hydralinks.cloud/) and click the "Install on Hydra" button, which will automatically add those sources to Hydra, allowing you to download your games. Some of them even let you play online as well!

![](/assets/img/thumbnail/hydra.png)

When you first download a game, you're not actually downloading the game itself; you're downloading a game "repack", which we talked about earlier. The cool thing about Hydra is it'll let you easily extract the game and run the repacks installer. Most repacks also let you install game dependencies such as a [`.net`](https://en.wikipedia.org/wiki/.NET) or [PhysX](https://en.wikipedia.org/wiki/PhysX) library. It's required to download those if you don't already have them, which the repack will prompt you to do.

After you install the game, you can delete the repack to save space. You can also go to the game in your library now, press play, and select the executable. You have now torrented a game!

![](/assets/img/thumbnail/hydraplay.png)

Be sure to support the developers, especially indie developers, if you enjoyed their game and have money to spare!

## WebTorrent/VLC (Movies and TV)
![](https://webtorrent.io/img/screenshot-player2.png)

It's cool you want to own your media rather than stream it! There are two ways you can do this;

1. Setting up qBittorrent and using [VLC](https://www.videolan.org/vlc/) or whichever media player to watch while you're downloading your piece of media
1. Using [WebTorrent](https://webtorrent.io/desktop/)! a free and open-source BitTorrent streaming application

For qBittorrent, all you have to do is start torrenting your piece of media and then play it within VLC! The only downside compared to streaming is you cannot fast-forward if that part hasn't been downloaded yet.

WebTorrent is even easier than this though, as it's a BitTorrent client that has its own video player built inside the application! just start torrenting your piece of media, and press play! you'll start watching it while it also downloads in the background!

## Streaming movies and TV

However, if you prefer streaming, then I recommend [FMovies](https://fmovies24.to/).

![](/assets/img/thumbnail/fmovies.png)

FMovies lets you stream media for free instead, without using your valuable hard drive space. However, in order to save space on their end as well, some movies and TV shows are only 720p. Not all of them, but it's something to consider.

For everything else, use [1337x.to](https://1337x.to/).

# I hope this post finds you well. Please take care of yourself.

![](/assets/img/thumbnail/1fe34eb7-b867-43b0-96ff-7212c5b10a3f.jpg)