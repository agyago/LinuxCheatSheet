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

