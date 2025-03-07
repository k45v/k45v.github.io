---
layout: post
title: Resizing the Ubuntu paritition in a Dual Boot Windows7 and Ubuntu 12.04 system
date: 2012-08-29
categories: [Linux]
---
I have a Dual boot system (Ubuntu 12.04 LTS and Windows7) with the GRUB as my bootloader. Lately, I have been using a lot of tools offered for Linux and I wanted to expand the partition size for my Ubuntu. I remember the last time when I tried to do this, using a partition manager in Windows; It did not end well. So this time I tried a different approach and it proved to be so easy that I decided to document it.

1. Boot into your Ubuntu OS. Then download the Ubuntu image file from [here](http://www.ubuntu.com/download/desktop). It would be an “ISO” file.
  <div class="text-center">
  {% include figure.html path="assets/img/download_ubuntu.jpg" class="img-fluid rounded w-75"%}
  </div>

{:start="2"}
1. Create a bootable USB stick using the instructions given [here](http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu)

1. Restart your PC and hit Esc or F12 (whatever takes you into boot menu) and select boot from USB device.

1. Click on Try Ubuntu. Now install gparted using the command below:
```shell
 sudo apt-get install gparted
```

1. Resize the windows partition which is at the end of the Windows file system to create un-allocated free space(in my case the partition did not hold the OS).

1. Resize the Ubuntu partition to use the created free space. (Now, GRUB stage 1 is no longer at the beginning of the parition).

1. Apply changes. It should take roughly 1.5min per GB of space allotted.

1. Now use Boot repair to fix the problems in the GRUB Bootloader (Instructions were borrowed from [How-To Geek](http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/)) :
```shell
sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair
boot-repair
```
Click on recommended repair.

1. Restart your computer and enjoy the expanded disk space in your Ubuntu OS.
<div class="text-center">
{% include figure.html path="assets/img/resize_ubuntu.jpg" class="img-fluid rounded w-75"%}
</div>
