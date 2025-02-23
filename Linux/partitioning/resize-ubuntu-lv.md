---
title: Resize ubuntu LV
description: 
published: true
date: 2025-02-23T20:00:30.601Z
tags: 
editor: markdown
dateCreated: 2025-02-23T20:00:30.601Z
---

I'm not really sure what you have done so far. The partition /dev/vda3 has been increased to 8.5 GB (which means 10GB of the disk are used), but the end of partition vda3 (20899839) is less than the end of the "physical" disk (23068672), see the output of fdisk -l. Maybe GPT PMBR size mismatch (20971519 != 23068671) gives some hint.

Anyway, parts of the LVM structures (pv and vg) are already reflecting the new size. What is missing is the size of the logical volume and the size of the filesystem. As you can see from `pvdisplay` and `vgdisplay`, there are 503 extents = 1.96 GiB still free.

So, first increase the size of the logical volume to that of the volume group:

`sudo lvextend -l 100%VG ubuntu-vg/ubuntu-lv`

`fdisk -l /dev/mapper/ubuntu--vg-ubuntu--lv` should then give you the new size of ~ 8.5 GB.

Now, increase the size of the filesystem to that of the logical volume (I suppose ext4 here for '/'; if it is a different filesystem, you will have to use a different command!):

`sudo resize2fs /dev/mapper/ubuntu--vg-ubuntu--lv`

This is possible for a mounted filesystem, when the kernel supports it, which all recent kernels should do.