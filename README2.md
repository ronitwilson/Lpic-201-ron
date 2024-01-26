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

