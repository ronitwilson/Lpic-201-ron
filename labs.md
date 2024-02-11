# 8-02-2024
## Configuring Network interfaces on Linux
* add scripts to /etc/sysconfig/network-scripts
* Using nmcli

# 10-02-2024
## Create and managing a software raid
* create a RAID 5 array
* fail active device and observe behaviour
* add new device to RAID

# 10-02-2024
## Troubleshoot cpu utilization
* debug applications freezing intermittently
* use systat package to diagnoise issue
* use free -h -> mem usage
* use iotstat 1 3 -> cpu usage
* use top -> see process details
* us ps -ef ->see process specific details

# 10-02-2024
## capacity usage reports
* need to justify the need to buy more hw resources
* use **systat service** , **sar**, **vmstat**, **iostat**
* install and use sysstat package
* Update the sysstat cron file -> (/etc/cron.d/systat)
  * example - */10 * * * * root /usr/lib64/sa/sa1 1 1
* 