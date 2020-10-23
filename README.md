# LinuxCheatSheet
common commands

| Command | Description |
| --- | --- |
| ls -lSr | Show files by size, biggest last |
| du -s * \| sort -k1,1rn \| head | Show top disk users in current dir |
| du -hs /home/* \| sort -k1,1h | Sort paths by easy to interpret disk usage |
| df -h | Show free space on mounted filesystem |
| df -i | Show free inodes on mounted filesystem |
| fdisk -l | show disks partition sizes and types (should be on root) |
| rpm -qa --qf '%10{SIZE}\t%{NAME}\n'\| sort -k1,1n | List all packages by installed size(bytes) |
| dd bs=1 seek=2TB if=/dev/null of=ext3.test | create a lasrge test file (be careful) |
| dpkg -query -W -f='${Installed-Size;10}\t${Package}\n'\| sort -k1,1n | List all package by installed size (debian) |
| | |
| tail -f /var/log/messages | Monitor messages |
| strace -c ls >/dev/null | profile calls |
| strace -fe open ls > /dev/null | list system calls |
| strace -fe trace=write -e write=1,2 ls > /dev/null | monitor write stdout and stderr |
| ltrace -fe getenv ls > /dev/null | list library calls |
| lsof -p $$ | List paths that process id has open |
| lsof ~ | list processes that have specified path open |
| tcpdump | show network traffic |
| ps -eo pid,args --forest | List process in a hierarchy |
| ps -eo pcpu,cpu,nice,state,cputime,args --sort pcpu \| sed '/^ 0.0 /d' | list process by % cpu usage |
| ps -e -orss=,args= \| sort -b -k1,1n \| pr -TW$COLUMNS | list process by mem usage (KB) |
| ps -C command_name -L -o pid,tid,pcpu,state | list all threads for a particular process |
| ps -p 1,$$ -o etime= | list elapsed wall time for particular pid |
| watch -n.1 pstree -Uacp $$ | display a changing process subtree |
| last reboot | system reboot history |
| free -m | show amount of remaining ram |
| watch -n.1 'cat /proc/interrupts' | watch changable data continuously |
| udevadm monitor | monitor udev events to help configure rules |
| | |
| uname -a | kernel version and system arch |
| head -n1 /etc/issue | show name and version of distribution |
| cat /proc/paritions | partitions registred on the system |
| grep MemTotal /proc/meminfo | RAM total seen by system |
| grep "model name" /proc/cpuinfo | cpu info |
| lscpi -tv | show pci info |
| lsusb  -tv | show usb info |
| mount \| column -t | list mounted filesystem |
| dmidecode -q \| less | display bios info |
| smartctl -A /dev/sda \| grep Power_On_hours | disk uptime
| smartctl -x /dev/disk | show all  information of disk |
| hdparm -i /dev/disk |  show info about disk data |
| hdparm -tT /dev/disk | read speed test on disk |
| badblocks -s /dev/disk | test for unreadable blocks |
| | |
| ethtool eth0 | show status of ethernet interface |
| ethtool --change eth0 autoneg off speed 100 duplex full | manually set ethernet interface speed |
| ip link show | list network interfaces |
| ip link set dev eth0 name "name" | rename interface eth0 to any name |
| ip link set dev eth0 up | bring interface eth0 up |
| ip a | show ip addr |
| ip route show | list routing table |
| ip route add default via "" | set default gateway to any IP set |
| ss -tupl | list internet services on a system |
| ss -tup | list active connections to/from system |
| smbtree | find windows machine |
| mount -t smbfs -o fmask=666,gues //windows/share /mnt/share | mount a windows share |
| | |
| sed s's/string1/string2/g' | replace string1 with string 2 |
| sed 's/\\(.*\)1/\12/g' | modify anystring1 to anystring2 |
| sed '/^\*#/d;/^\*$d' | remove comments and blank lines |
| grep -Ev "^#\|^$" file | remove comments and blank lines (grep) |
| sed ':a;/\\\$/N; s/\\\\n//; ta' | concat lines with trailing \ |
| sed 's/\\([\`"$\\]\\)/\\\\1/g' | escape shell metachar active within double quotes |
| sed 's/[\\t]\*$//' | remove trailing spaces from lines |
| seq 10 \| sed "s/^/ /; s/ \*\\(.\\{7,\\}\\)/\\1/" | right align numbers |
| seq 10 \| sed p \| paste -- | duplicate a column |
| sed -n '1000{p;g}' | print 1000th line |
| sed -n '10,20p;20g' | print lines 10 to 20 |
| sed -n 's/.\*<title>\\(.*\\)<\\/title>.\*/\\1/ip;T;q' | extract title from html web page |
| sed -i 42d ~/.ssh/known_hosts | delete 42nd line |
| echo 'Test' \| tr '[:lower:]''[:upper:]' | case convertion |
| tr -s '[:blank:]''\\t'</proc/diskstats \| cut -f4 | cut fields separated by blanks |
| seq 10 \| paste -sd '' | concat and separate line items to a single line |
| | |
| sort -u file1 file 2 | union of unsorted files |
| sort file1 file2 \| uniq -d | intersection of unsorted files |
| sort file1 file1 file2 \| uniq -d | diference of unsorted files |
| sort file1 file2 \| uniq -u | symmetric difference of unsorted files |
| join -t'\\0' -a1 -a2 file1 file2 | union of sorted files |
| join -t'\\0' file1 file2 | intersection of sorted files |
| join -t'\\0' -v2 file1 file2 | difference of sorted files |
| join -t'\\0' -v1 -v2 file1 file2 | symmetric difference of sorted files |
| | |


