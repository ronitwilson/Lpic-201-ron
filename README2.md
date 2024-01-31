# 26-01-2024
## Advanced Storage and adminstration
### using an iSCSI Target and initiater
* IT is for network storage -> involves using a initiator(client) and target(server)
* targetcli -> shell for viewing, editing, saving the conf of kernel target subsystem
  * create a backstore using nvme1n1 
  * create a target from storage ip ?
  * create a acl, lun(logical unit number), portal(ip/port  pair for iscsi target)
* Important files
  *  iscisid.conf, initiator.iscsi, iscsid(systemd daemon),scsi_id used with udev
*  iscsiadm -> admin utility tool
*  targetcli -> used for configuring the target example
  *  example -> bloxk create block01 /dev/nvme1n1
*  iScsi structure`
  *  ![image](https://github.com/ronitwilson/Lpic-201-ron/assets/9934360/6b44603f-2936-418a-993b-2061c3ccb85f)

# 27-01-2024
## Creating and managing Logical volumes
* Suppose there are 2 pen drives with 16gb but one file of 20 gb we can solve this problem with logical volumes
 * ![image](https://github.com/ronitwilson/Lpic-201-ron/assets/9934360/88fe4dd3-a79f-44ac-aff8-2f6cf2882895)
* pvcreate -> create **physical volume**
* pvscan -> scan all supported LVM ,
* pvdisplay -> shows info
* lvcreate -> create a logical volume
* vgcreate -> create a volume group
* **Steps**
 * pvcreate /dev/nvme11p{1,2}
 * vgcreate data_vg /dev/nvme1n1p{1,2}
 * lvcreate -L 200 -n backup data_vg
 * lvcreate -L 20 -n backup_2 data_vg
 * lvdisplay
 * mkdir /mnt/backup
 * mount -t ext4 /dev/data_vg/backup /mnt/backup
 * Further we can use lvreduce,lvextend to resize the lv size

# 31-01-2024
## cerating and using snapshots
* lvcreate -s -> create a snapshot
* lvchange  -an /dev/data_vg/current
* lvconvert --merge data_vg/cu_snap1 -> this merges the snapshor to the /data_vg/current from which the snapshot was taken

## system maintenance
### taking backups / Installing and patching a program from source
* /usr/src -> used as a reference for program source codes, not ment to be build here
* /usr/local -> ofr installing software locally
* /opt-> installation of add-on apps
* gzip -> .gz, .z, .tgz
* bzip2 -> .bz2, .bz, .tbz
