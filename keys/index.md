# Key bindings

[Vimwiki](Vimwiki)
[Vim](Vim)
[Top](Top)
[atop](atop)
[glances](glances)

## Manual, Investigation

```
man -K keyword # brute force search for keyword
help           # bash internals
whence -wm '*' # zsh shows what shell knows - commands, functions, reserved words..
type for       # check what type is keyword
```


## Fzf

```
packtree <libName>     #

^r                     # search in history
^t                     # fzf search in current directory
cd **<tab>             # fzf autocomplete
ssh **<tab>            # fzf autocomplete
rm ^t                  # fzf you can select multiple files to delete
kill -9 <tab>          #
unset **<tab>          #
export **<tab>         #
unalias **<tab>        #
fzf --preview 'cat {}' # fzf search with preview, can be used any editor including nvim
print -z "stsdth       # puts argument onto the editing buffer stack
```

## Systemd

```
journalctl _COMM=<tab>
journalctl -t kernel
journalctl -p2 # show messages critical and worse
journalctl --list-boots
journalctl -S 01:00:00 -U 01:10:05 # show since until, can be with full dates
journalctl --since 2017-12-20 --until 2017-12-24
journalctl --since yesterday -u NetworkManager
dmesg # logs that goes to journalctl too, but shorter in live time
man systemd.journal-fields                     # fields to match by
systemd-cat # systemd specific logging
logger "message to log" # logger message to system log(systemd journal if systemd), seems better than systemd-cat

systemctl                                      # load all loaded and active systemd units
systemctl list-units                           # list units that systemd currently has in memory
systemctl list-unit-files                      # see which are enabled
systemctl list-unit-files -t [timer,mount]
systemctl --all -t service                     # list all serice units whether they are active or not
systemctl list-mounts
systemclt list-timers

systemctl status                               # shows tree overview
systemctl status multi-user.target             # target status
systemctl status default.target                # target status
systemctl --failed                             # shows system status, like degraded
systemctl list-dependencies –after ssh.service # get services that ran after ssh

systemctl start logwatch.timer
systemctl enable logwatch.timer
logwatch --detail 10 | less
logwatch --service systemd | less
logwatch --range today | less
systemd-analyze calendar 2030-06-17 # helper for setting time with timers


ls -al /lib/systemd/system/runlevel*
cd /lib/systemd/system
cd /etc/systemd/system
systemctl get-default                          # get default runtime level
systemctl daemon-reload

systemctl isolate multi-user.target            # to move between different runtime targets
systemctl isolate graphical.target

systemd-analyze blame # longest initializing services list
systemd-analyze plot > system.svg

crontab -l
crontab -e                                     # lets edit cronjobs and after save restarts daemon
/etc/anacrontab                                # jobs that intended to run in specific intervals(will be ran even if time was missed)
at now +2 minutes                              # delayed job run, Ctrl+D to finish
atq                                            # show what jobs to be run
atrm <jobNmb>                                  # remove job
```



## Various

```
tar -xvf <fileToExtract <whereToExtract>                            # extract archive to specific folder
xclip -sel clip id_rsa.pub                                          # copy file content to clipboard

ln -s <pathToFile> <pathToLink>                                     # create soft link

pacman -Ql package_name                                             # list files belonging to package
pacman -Qi                                                          # show installed packagies
pacman -Qi package_name                                             # show package info including what depends on package and it's dependencies
pacman -Qe                                                          # show only programs that you explicitly installed
pacman -Qdt                                                         # orphan dependencies
pacman -Qo file                                                     # find to which package file belongs
pacman -Syu                                                         # download fresh copy of master package database and upgrade every package #maintenance
pacman -Sii                                                         # rever dependencies #
pacman -Si                                                          # dependencies of remote packages
pacman -Sc                                                          # remove cache of old packages #maintenance
pacman -u file.tar.gz                                               # install from package
pacman -Rns <package_name>                                          # remove package with dependencies if they are not used elsewhere
pacman -Rdd <package_name>                                          # remove package, ignoring it's dependencies
yay -Si xmonad                                                      # show extensive info about package
yay -Sua                                                            # update AUR packages
yay -Pu                                                             # give updatable packages
yay -Yc                                                             # removes uneeded dependencies #maintenance
yay -Ps                                                             # print package information summary
yay -Syu                                                            # like pacman + updates AUR packages

cat * | grep -v "^$"                                                # exclude lines which start with dollar sign
coproc (zathura "$booksFolder/$1 &)                                 # for running commmand as separate process

echo "sth\nhello\n" | tr '\n' ' '                                   # translate(replace) all new lines with spaces
echo b{ed,olt,ar}                                                   # beds bolts bars
echo testfile{0,1,2,3,4}.txt                                        # testfile0.txt testfile1.txt...
echo test{0..20}{a..f}                                              # cycle in cyle
ls *e.?6?*.asc                                                      # file globbing
ls *[0-9][a-fgh][!m-o]*
ls | column
ls -t                                                               # sort by time
mv -t <dir> file1 file2 file4*.txt                                  # move multiple files


find . -type f -empty ! -name "*test.file*"                         # ! inverts name filter
find / -type f -links 4                                             # find all files with 4 harldinks
find /usr -inum 531003                                              # find files with inode 531003
find /usr -samefile /usr/sbin/mkfs.ext3
find ./ -type f -exec sed -i 's/foo/bar/g' {} \;                    # replace in all files foo to bar

w                                                                   # show logged users and what are they doing
who                                                                 #
whoami                                                              # current user
id
tty                                                                 # print device of terminal
/etc/passwd
/etc/shadow                                                         # passwd moved to shadow, it's safer as it can be read only by root
openssl passwd -6 mypassword
pwgen                                                               # password generator
/etc/group
/etc/login.defs                                                     # configuration for new users
/etc/default/useradd                                                # configuration for new user
/etc/skel                                                           # files that would be copied to new users home dir
/etc/security/pwquality.conf                                        # password requirements
useradd -c "Test user" -d /TestFS/testuser -s /usr/bin/zsh testuser # create user
usermod -e 2019-06-05 testuser                                      # expire user password on defined date
userdel -r testuser                                                 # delete user with home dir
pkill -KILL -U student1                                             # kill all user processes

tty                                                                 # on one console
echo "hello" > /dev/pts/2                                           # send message to other terminal

cat test.pdf > /dev/usb/lp0                                         # print directly to printer device

lscpu
lsblk
df -h
dumpe2fs /dev/sda1                                                  # lots of deep info about filesystem (cylinder group info, inodes, blocks etc
e2label /dev/sda1 MyBoot                                            # give label to disk
fsck                                                                # for fixing disk and getting report, if any problems, systemd runs it automatically

script fileName                                                     # creates session in which it records everything what was done and outputed

stat <fileName>                                                     # statistics about file - times, size, inode..
cal                                                                 # calendar for this month

info coreutils                                                      # gnu core utils
yes stringThatWouldConstantlyRepeat                                 # infinite stream - could be used for maxing out file
dd if=/dev/sdb1 bs=512 count=1                                      # print to console first 512 bytes (could be used to read write MBR)
dd if=/dev/mem bs=2048 count=100 | od -c                            # read from ram
/dev/null                                                           # most often for getting rid of unwanted output
/dev/zero
cat /dev/urandom                                                    # infinite stream of random symbols, could be used to overwrite data to be unrecoverable
shred                                                               # for overwriting individual files, partitions, drives
fc                                                                  # open last command in editor

pacman -Sq [<groupName>]                                            # remote groups of software

top
atop
htop
glances
iotop
ps
free
vmstat
iostat -j ID 

                                                                    # results can be questionable - inacurate or wrong because, because hardware vendors not always cooperates
lshw
dmidecode -t 2                                                      # DMI(Desktop Managment Interface)system's hardware components description, uses SMBIOS info(data collection performed by BIOS)
lsusb -v | less
lsusb -t                                                            # tree
usb-devices                                                         # same as lsusb but more
lspci -v | less

bc                                                                  # calculator



sensors                                                             # temperature sensors
sensors-detect

smartctl -x /dev/nvme0n1                                            # disk health report
hddtemp

sar                                                                 # system activity reporter
sar -u 1 3                                                          # show cpu every 1 sec for 3x
sar -r                                                              # memory stats
sar -b                                                              # disk stats
sar -w 1 3                                                          # context switches
sar -n [DEV, TCP, UDP ... ALL]                                      # network usage
sar -A | less                                                       # show everything
/var/log/sa                                                         # stats data location

shopt                                                               # bash options

grub-install --version


ll /usr/lib/systemd/system/*dm.service                              # list display managers
ll /etc/systemd/system/display-manager.service                      # see what display manager is set

seq -w 20                                                           # generate sequence from 01 to 20

chown
chgrp
chmod 640 file0[4-7]
chmod g+rx,g-w file1, file2

groupadd -g 5000 dev                                                # works only after log out
usermod -G 5000 [student](student)                                  # works only after log out
gpasswd -M student,student1 dev                                     # works only after log out
tail /etc/group

umask                                                               # default permissions to all created files(/etc/profile) - reverse logic - what permissions not to set, and x is never set


strings /bin/ls                                                     # print files printable symbols

udevadm monitor                                                     # monitor udev events
udevadm info -a -n /dev/sdb | less                                  # query udev db for device info
udevadm control --reload                                            # reload after adding scripts and similar changes
dmesg | tail | grep -i sd                                           # kernel ring buffer messages
/usr/lib/udev/rules.d/                                              # udev default naming rules
/lib/udev/rules.d/                                                  # udev local naming rules

dd -if=/dev/sda of=/tmp/myMBR.bak bs=512 count=1                    # backup MBR
dd if=/tmp/myMBR.bak of=/dev/sda                                    # restore mbr record

ssh root@myHost
ssh -L 80:intra.example.com:80 gw.example.com                       # local port forward
sshfs -o idmap=user user@serverHost: ~/myDirForFs                   # home dir(nothing after ':' to local ~/myDirForFs mapping
echo "ServerAliveInterval 60" >> ~/.ssh/config                      # for staying connected and pinging every 60s
fusermount -u ~/myDirForFs                                          # for unmouting sshfs

renice +1 <pid>

lpinfo -v                                                           # used to list all of the available buses, protocols and any printers attached to each

od -c -N 1000 < /dev/urandom                                        # octal display
unix2dos -n cpuHog cpuHog.dos
unix2mac
wvText                                                              # used to convert MS Word docs to text format
odt2txt

watch <commands>                                                    # monitor program output
time  <commands>                                                    # for time calculation

chronyc tracking
chronyc sources

lsattr                                                              # list Ext2-Ext3-Ext4 attributes
chattr

curl wttr.in                                                        # get weather forecast in console

last                                                                # show a listing of last logged in users
lastb                                                               # all bad login attempts

firewall-cmd --list-ports [--permanent]                             # list existing rules, permanent show rules that will be active after restart
firewall-cmd --add-service=telnet
firewall-cmd --remove-service=telnet
firewall-cmd --list-services
firewall-cmd --list-services [--permanent]
firewall-cmd --runtime-to-permanent                                 # save all configuration

iptables-save                                                       # list rules
iptables -I INPUT 5 -p tcp -m state --state NEW -m tcp --dport 23 -j ACCEPT; iptables-save




sxiv -t *.jpg                                                       # thumbnail
ls *.jpg | sxiv -tio                                                # use it to select images and get selected imgs list
```

## Sbt

```
sbt "whatDependsOn com.adform.dp storm-commons-core" | less -R
sbt provided:dependencyBrowseGraph # not test only dependencyes and no provided ones
sbt test:dependencyBrowseGraph
sbt "inspect test:compile"
sbt "inspect tree" | less -R

sbt "~compile" # recompile on code change
sbt "show fullResolvers" # show all resolvers of project
```

## Zathura

```
:bmark <name>         " set or overwrite bookmark
:blist                " list bookmarks
:blist <bookmarkName> " go to specified bookmark
<tab>                 " table of content
```
## Git

```
git status
git add -a -m "commit msg" # add all and commit
git checkout -b "new branch name"
git push origin branchName
git reset                  # unstage all staged files
git add ^t                 # fzf autocomplete
git restore <file>...      # restore/undo changes in file
```

## Network

```
ip neigh # show neighbour  networks, if one, probably gateway
ping -c2 _gateway

ip addr show enp0s3
ip link set enp0s3 down
/etc/resolv.conf
/etc/hosts

ip route # route table
traceroute www.google.lt
tcpdump -i enp0s3
mtr -n www.google.lt # instead of traceroute, packet loss could indicate a problem
whois 78.56.127.254 # shows extended info about ip owner
dig # dns lookup utility, shows all ips that dns routes to

iptraf-ng # traffic monitor and more, GUI program analog - wireshark
/etc/sysconfig/network-scripts
nmcli
nmcli connection add save yes type ethernet ifname enp0s3 con-name enp0s3 ip4 10.0.2.11/24 gw4 10.0.2.1 ipv4.dns "10.0.2.1 8.8.8.8" # setting static ip
```
