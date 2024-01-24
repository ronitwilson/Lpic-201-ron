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

# 11-29-2023
## Systemd mount units
* systemd works with etc/fstab 
* THe systemd mount unit ends with .mount
   * Inside /run/systemd/generator we can find these mount file
* We can see status,stop, start on that .mount unit file
## ext2/3/4 filesystem
### EXT filesystem
* ext2 supports upto 2TB, 32000 sub dirs
   * no overhead caused by journaling
   * can be converted to ext3
* ext3 differences on the journalling
* ext4 max file size upto 16TB
* **mkfs tool** for building filesystem
* **fsck tool** check and repair linux filesystem
* **tuen2fs** adjust tunable params of fs
   * Set the volume label, add journal params  etc
*  **debugfs** debuger of Fs
*  Xfs filesystem
   * extens filesystem , change int he way blocks are allocated and managed
* **dump32fs** prints the super block and block info

# 02-12-2023
## filesystem
* xfs_repair command
* Xfs dump and restore command
   * There is various levels of backup
      * level 1-9
         * level 1 backup would be the incremental backup after a full backup
         * a max of 9 such backup is possible         

## Btrfs and Zfs filesystem
* btrfs focuses on fault tolerence
* It is copy on write filesystem -> when a change is made to file it retains the old file n saves the changes alone on another space
* btrfs-convert command to convert ext2/3 fs to btrfs
* It can be partof multiple discks (?? like part of the fs in one usb n remaining in another usb )
   * For the os it will show as 1 fs mounted in a path, but actullay will be using more than one partition/disk
* More than one subvolumes can be created and mounted
   * Typically there will be 1 volume in ext2 is my understanding
   * btrfs supports creating multiple sub volumes    
* Zfs filesystem
   * combines the feature of copy on write filesystem and volume manager

# 04-12-2023
 ## AutoFs
 * Indirect mount and direct mount
 *  /etc/auto.master
    * /mnt/indirect /etc/auto.indirect <options>
       * inside auto.indirect
          * backup -fstype=ext3,ro :/dev/nvme1n1p2
          * current -fstype=xfa,ro :/dev/nvme1n1p3
    * direct mount
       * /- /etc/auto.direct --timeout=600
       * inside auto.direct
          * /mnt/direct -fstype=btrfs:/dev/nvme1n1p


# 9-12-2023
## CD rom filesystem
   * There is something called cd rom filesystem
      * ISO 9660
      * Universal Disk format
      * Hierarchical file system
## Data Encryption
   * Linux Unified key setup
      * It is a disk encryption spec
         * It uses the dm-crpt kernel module
         * **cryptsetup** ->main command for data encrypt->def: setup cryptographic volumes for dm-crypt -> we can create a fs inside the volume
## SMART Devices
   * smartd -> a daemon that monitors the (SMART) system built inot ATA,IDE and SCSI-3 hard drices
      * It can notify incase of errors
   * there is a smartctl tool


# 11-12-2023
## Creating swap space [LAB]
* Create and enable a swap partition using /dev/xvdg1.
* Add an entry to /etc/fstab to ensure that the swap partition persists though a reboot (use the UUID)
* Create and enable a 1 GB swap file in the root directory called "extraswap".
* Add an entry to /etc/fstab to ensure that the swap file persists through a reboot (use the full path to the file name).

# 19-12-2023
## Measuring system resources
* There is something called Cpu util and device util(memory, disk usage, paging etc). 
* IOSTAT, SAR, vm stat, free commands
* The **sysstat** service normally provides all these tools
* we can run these commands with an interval n count eg  iostat 1 5

# 29-12-2023
## More commands to measure system resources
* lsof -> view all open files 
   * lsof -i -> lists all open files based on network connections 
   * lsof -D /var -> list all open files in that directory
* ps, -> list process

# 07-01-2024
## PS command
* ps -fC sshd
* ps tree -> shows all the process are in graphical tree view
* Top command
   * we can see the field view by clicking the f key
   * we can kill a process by typing k

# 10-01-2024
## Measuring network usage
* netstat command
   * netstat command is obsolete n replaced by ss command
   * main option n,p,l (numerical address(does not resolve host name), shows pid, shows listening sockets)
* w commnad
   * shows current time and how long the system has been running
* uptime command
   * shows how long the system is running
 
# 13-01-2024
## Measuring system resources
* nagios
   * agent mode
   * snmp mode agentless mode
* icinga2
   * fork of nagios
* mrtga
   * monitor the network usage, uses snmp protocol
* cacti
   * works together with rrd tool
* collectd
   *Has plugins based on the resource we want to monitor

  # 16-01-2024
  ## configuring collectd
  * cofigure /etc/collectd/collectd.conf  with the hostname etc
  * we shoulde configure cgi.load  which is a apache2 mod n copy some files to make collectd available voa apache server
  * We can use such tools to figureout how the capacity is being used
  * Collectd can also be used to collect application data n see over network (but no detailed explain)

# 20-01-2024
  ## Understanding Raid
  * Striping(multiple device presented as single device), mirroring(prvides backup), block level stripping
  * ![image](https://github.com/ronitwilson/Lpic-201-ron/assets/9934360/4e2fea55-974f-40c1-a8e8-1bea9dc457de)
  * 0xFD partition type for RAID partition
  * /proc/mdstat -> displays snaphot of kernels RAID/md state

# 24-01-2024
  ## Managing Fail over and Recovery of RAID device
  * use cat /proc/mdstat -> to check the raid state
  * create filesystem on the raid partition using -> mkfs.ext4 /dev/md0
  * mount the partiton to dir /mnt/raid -> mount -t ext4 /dev/md0 /mnt/raid
  * create some files in that folder -> using touch
  * fail the raid using command -> mdadm -f  /dev/md0 /dev/nvme1n1p1
  * Raid recovers by recovering the spare partition
  * add more partition to the raid config madadm -a /dev/md0  /dev/nvm1/p4 /dev/nvm1/p5
     * run this to rebuild the raid config to retain after reboot -> mdadm -D -s -v > /etc/mdadm.comf
   
## Working with Physical Storage devices
* DMA and interrupt handling
   *  cat /proc/interrupts
   *  ls -l /proc/irq
   *  ![image](https://github.com/ronitwilson/Lpic-201-ron/assets/9934360/816a1749-d416-453f-8d26-d621547410f0)
*  hdparm utility -> for STATA/IDE devices
   *  devices of this type will be /dev/hd*
   *  -I more info
   *  -t for testing timings of device
*  sdparm -> for SCSI/SATA
   *   --commnad=CMD sends SCSI command on device
*  nvme utility -> for pci express-based devices
   *   smart-log -> retrive smart log
   *   list -> lists all nvme controllers
*   fstrim ->discard unwanted block on mounter FS
   *   discard option in /etc/fstrab ofr automatic trim ( **not recommended** )

