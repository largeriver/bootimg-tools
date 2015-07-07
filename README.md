bootimg-tools
=============

Android boot.img creation and extraction tools (also MinGW compatible)

Based on the original Android bootimg tools from:
  https://android.googlesource.com/platform/system/core

原项目代码与AndroidL不兼容，主要是两点
* 解包时没有考虑按照pagesize对齐
* 不支持 dt.img,也就是 data device tree


steps

1. unmkbootimg -i boot.img
2. mkdir ramdisk_dir && cd ramdisk_dir 
3. gunzip -c  ../ramdisk.cpio.gz | cpio -i
4. edit files under ramdisk_dir
5. find . | cpio -o -H newc | gzip > ../newramdisk.img
6. cd .. 
6. mkbootimg with args 
