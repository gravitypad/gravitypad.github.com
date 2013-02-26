---
layout: post
title: "Reclaiming disk space from Outlook OST files"
date: 2010-02-09
comments: true
categories: 
popular: true
---
I recently received a warning for Windows telling me I was dangerously low on disk space on my laptop’s C: partition. I intentionally don’t put a lot on my C: because I like to be able to pave my machine’s OS frequently without having to worry about backing up my data, so my C: partition usually only has the OS and applications. I have 40 GB dedicated to my C: partition, and I have never bumped up against any space constratints.

I ran [WinDirStat](http://windirstat.info) to see what was taking up so much space. Aside from the usual suspects (pagefile.sys and hiberfil.sys), I saw two large files, below in green (the two reds are pagefile.sys and hiberfil.sys)

![](/images/posts/outlook/1.jpg)

Turns out they are two OST files connected to my two Exchange accounts (Outlook 2010 lets you have multiple Exchange accounts in a single profile - very cool!). Each OST was using over 10 GB of space! I frequently archive my mail to PST files (located on another partition), so I was surprised the OST’s were so big.
The solution was to compress the OST files. I had forgotten that you can compress not only PSTs but also OSTs. Here’s the steps: (Again, this is Outlook 2010. Previous version may be slightly different.)

1. Close Outlook.
2. Open the Mail control panel applet.
3. Click the Data Files button.
4. Select the file associated with your Exchange account. It’s named with your default email address.

    ![](/images/posts/outlook/2.jpg)
 
5. Next, click the Outlook Data File Settings button.

    ![](/images/posts/outlook/3.jpg)

6. Finally, click Compact Now. Sit back and wait - It takes a while. For my 10GB file, which compressed down to about 5GB, it took about 3 hours.
    ![](/images/posts/outlook/4.jpg)
 
I was able to quickly reclaim 11GB of disk space on my C: partition by compressing my OST files. Hopefully this will help someone else with the same predicament!

