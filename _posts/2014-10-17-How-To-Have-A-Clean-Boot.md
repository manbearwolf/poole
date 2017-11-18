---
layout: post
title: "How To Have A Clean Boot Of Windows 8.1 with UEFI Mode Enabled"
date: 2014-10-17
tags: [software]
author: Matthew Bott
---

On my new netbook, I discovered you need to do more than just create a boot-able .iso of Windows 8.1, for it to load correctly in BIOS.  Legacy BIOS mode is great, but not as good and as fast as UEFI made for Microsoft Windows. Which is used in newer computers using Windows 8.1.  You need to download a program called Rufus 1.4.10.514, to go around this problem, otherwise, you need to change your BIOS <kbd>(F2)</kbd> at boot and change the setting to Legacy BIOS, which will run anyway, but not as good as UEFI.

<!--more-->

* <a href="https://rufus.akeo.ie/" rel="nofollow" target="_blank" title="Rufus Website">https://rufus.akeo.ie/</a>
* (<a href="https://rufus.akeo.ie/downloads/rufus-2.17p.exe" rel="nofollow" target="_blank" title="Direct Download">Download Rufus</a>)

Rufus is like any other .iso loader, except you can change settings for the UEFI partition, that is created nowadays in Windows.

You will want to download the windows .iso and choose the settings **<u>GPT partition scheme for UEFI computer</u>** and load the .iso file. This all loads onto a bootable USB.

<center>
<img src="https://res.cloudinary.com/mbott1982/image/upload/v1510083618/BlogInnMin/posts/rufus/rufus-min.png" title="ScreenShot Rufus" caption="Rufus" />
</center>

**That's it!**<br />
It should boot windows and install with UEFI Enabled.  This makes the entire complicated problem of this stuff simple and easy.

<a href="https://www.wikihow.com/Have-a-Clean-Boot-of-Windows-8.1-with-UEFI-Mode-Enabled" target="_blank" rel="nofollow" title="Expired Same Article On wikiHow">wikiHow Stub Article Link</a>
