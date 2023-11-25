# Lpic-201-ron

# 11-22-2023
## Linux system startup
* Using fsck tool 
* Booting to specified run level for recovering system
    * We can use systemctl isolate rescue.target

# 11-23-2023
## Linux system startup
* Conlusion Lesson
    * UEFI has a uefi shell which can be used to launch efi apps 
    * Grub 2 uses the template in /etc/grup.d n /etc/default/grub to get grub.cfg
 

# 11-25-2023
## Filesystem mounts
* Mounting
   * /etc/fstab, /etc/mtab, /proc/mounts
   * mount, umount, sync command
   * Sync command no longer that significant since the write speeds have improved very much
   * blkid command -> finind the uuid of devices
   * /etc/fstab
      * Field 1 -> descrive through uuid the device
      * 2 -> mount point (eg /)
      * 3 -> type of fs (xt4, fs)
      * 4 -> mount opitons (eg defaults)
      * 5 -> used by dump to dtermine which filesystem needs to be dumped used for backup (0 disables)
      * 6 -> determines oderder in which filesystem checks needs to be done(rootfs set to 1 all other set to 2, default 0)
   * etc/mtab
      * umount and mount maninded this list (nowadays symlink to proc/mount or /proc/self/mounts
   * just mount command prints a lot of details
