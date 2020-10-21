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
