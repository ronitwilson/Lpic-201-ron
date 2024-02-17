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
 *  Create the iSCSI target with the following unique IQN
 *  create lun for the block
 *  create acl
*   iSCSI Initiator
 *   add initiator name in vim /etc/iscsi/initiatorname.iscsi
 *   Discover the iSCSI target
 *   scan target
 *   Connect to the target:
 *   Verify that iscsi is running 

# 14-02-2024 
## Analyzing nw traffic on Linux
### explore nmap,ss, lsof, and tcpdump
#### Scan for Open Ports
* use nmap to scan for open tcp port ->  **nmap -F <ip>**
* **nmap -sT -F 10.0.1.10**
#### Analyze the Listening Sockets
* ss -tulnp
* lsof | grep ssh | wc -l -> total number of files opened by ssh
#### Perform packet capture
* tcpdump -D -> see which packets are able to capture packets
* Doing packt capture
 * tcpdump -i ens7 -c 5 -w test.pcap
 * tcpdump -r test.pcap
 * 

# 17-02-204
## Compiling a Program from Source
### You have been tasked with setting up a system with the two web servers that are under consideration: nginx and httpd. In order to complete this task, you will need to obtain the source code tarballs and extract them in /usr/local/src. Once extracted, you will need to install nginx to /usr/local/nginx, being sure to exclude the rewrite and gzip modules. Be sure that nginx is functioning properly before installing and testing the httpd server. Then, you will need to install httpd to /opt/httpd-2.2.9 and ensure that is working as expected.
* use wget to download the source
* run ./configure with flags
 *  ./configure --prefix=/usr/local/nginx --without-http_rewrite_module --without-http_gzip_module
 *  ../configure --prefix=/opt/httpd-2.2.9
*  make
*  make install
 *  file found insdie /usr/local/nginx/sbin
 *  file found inside /opt/httpd-2.2.9/bin/
