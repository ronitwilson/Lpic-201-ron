# 8-02-2024
## Configuring Network interfaces on Linux
* add scripts to /etc/sysconfig/network-scripts
* Using nmcli

# 10-02-2024
## Create and managing a software raid
* create a RAID 5 array
* fail active device and observe behaviour
* add new device to RAID

# 11-02-2024
## Troubleshoot cpu utilization
* debug applications freezing intermittently
* use systat package to diagnoise issue
* use free -h -> mem usage
* use iotstat 1 3 -> cpu usage
* use top -> see process details
* us ps -ef ->see process specific details

# 11-02-2024
## capacity usage reports
* need to justify the need to buy more hw resources
* use **systat service** , **sar**, **vmstat**, **iostat**
* install and use sysstat package
* Update the sysstat cron file -> (/etc/cron.d/systat)
  * example - */10 * * * * root /usr/lib64/sa/sa1 1 1
* 

# 12-02-2024 
## Configuring isci on Linux
* ON target machine
 * install targetcli 
 *  create the block01 and block02 backstore from /dev/xvdf and from /dev/xvdg
 *  create lun for the block
 *  create acl
 *  

# 14-02-2024 
## Analyzing nw traffic on Linux
### explore nmap,ss, lsof, and tcpdump
#### Scan for Open Ports
* use nmap to scan for open tcp port ->  **nmap -F <ip>**
* **nmap -sT -F 10.0.1.10**
