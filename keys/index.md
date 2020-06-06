# Key bindings

[Vimwiki](Vimwiki)
[Vim](Vim)
[Top](Top)

## Manual, Investigation

```
man
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
git add ^t             # fzf autocomplete
kill -9 <tab>          #
unset **<tab>          #
export **<tab>         #
unalias **<tab>        #
fzf --preview 'cat {}' # fzf search with preview, can be used any editor including nvim
print -z "stsdth       # puts argument onto the editing buffer stack
```

## Systemd

```
cd /etc/systemd/system
journalctl _COMM=<tab>
man systemd.journal-fields                     # fields to match by

systemctl list-units                           # list units that systemd currently has in memory
systemctl list-unit-files                      # see which are enabled
systemctl status                               # shows tree overview
systemctl --failed                             # shows system status, like degraded
systemctl list-dependencies –after ssh.service # get services that ran after ssh

ls -al /lib/systemd/system/runlevel*
systemctl get-default                          # get default runtime level

systemctl isolate multi-user.target # to move between different runtime targets
systemctl isolate graphical.target
```



## Various

```
tar -xvf <fileToExtract <whereToExtract>          # extract archive to specific folder
xclip -sel clip id_rsa.pub                        # copy file content to clipboard

pacman -Ql package_name                           # list files belonging to package
pacman -Syu                                       # download fresh copy of master package database and upgrade every package
pacman -u file.tar.gz                             # install from package
pacman -Qo file                                   # find to which package file belongs
pacman -Rdd <package_name>                        # remove package, ignoring it's dependencies
pacman -Sii                                       # rever dependencies #
pacman -Si                                        # dependencies of remote packages
pacman -Qi                                        # show installed packagies

cat * | grep -v "^$"                              # exclude lines which start with dollar sign
coproc (zathura "$booksFolder/$1 &)               # for running commmand as separate process

echo "sth\nhello\n" | tr '\n' ' '                 # translate(replace) all new lines with spaces
echo b{ed,olt,ar}                                 # beds bolts bars
echo testfile{0,1,2,3,4}.txt                      # testfile0.txt testfile1.txt...
echo test{0..20}{a..f}                            # cycle in cyle
ls *e.?6?*.asc                                    # file globbing
ls *[0-9][a-fgh][!m-o]*
ls | column
mv -t <dir> file1 file2 file4*.txt                # move multiple files


find . -type f -empty ! -name "*test.file*"       # ! inverts name filter
find / -type f -links 4                           # find all files with 4 harldinks
find /usr -inum 531003                            # find files with inode 531003
find /usr -samefile /usr/sbin/mkfs.ext3


w                                                 # show logged users and what are they doing
who                                               #
whoami                                            # current user
id
tty                                               # print device of terminal

tty                                               # on one console
echo "hello" > /dev/pts/2                         # send message to other terminal

cat test.pdf > /dev/usb/lp0                       # print directly to printer device

dmesg                                             # print or control kernel ring buffer
lscpu
lsblk
df -h
dumpe2fs /dev/sda1                                # lots of deep info about filesystem (cylinder group info, inodes, blocks etc
e2label /dev/sda1 MyBoot                          # give label to disk
fsck                                              # for fixing disk and getting report, if any problems, systemd runs it automatically

script fileName                                   # creates session in which it records everything what was done and outputed

stat <fileName>                                   # statistics about file - times, size, inode..
cal                                               # calendar for this month

info coreutils                                    # gnu core utils
yes stringThatWouldConstantlyRepeat               # infinite stream - could be used for maxing out file
dd if=/dev/sdb1 bs=512 count=1                    # print to console first 512 bytes (could be used to read write MBR)
dd if=/dev/mem bs=2048 count=100 | od -c          # read from ram
/dev/null                                         # most often for getting rid of unwanted output
/dev/zero
cat /dev/urandom                                  # infinite stream of random symbols, could be used to overwrite data to be unrecoverable
shred                                             # for overwriting individual files, partitions, drives
od -c -N 1000 < /dev/urandom                      # octal display
fc                                                # open last command in editor

pacman -Sq [<groupName>]                          # remote groups of software

top
atop
htop
glances
iotop
free
vmstat
iostat -j ID 
lsusb -v | less
lspci -v | less

                                                  # results can be questionable - inacurate or wrong because, because hardware vendors not always cooperates
lshw
dmidecode -t 2

sensors                                           # temperature sensors
sensors-detect

smartctl -x /dev/nvme0n1
hddtemp

sar                                               # system activity reporter

shopt                                             # bash options

grub-install --version


ll /usr/lib/systemd/system/*dm.service            # list display managers
ll /etc/systemd/system/display-manager.service    # see what display manager is set

seq -w 20                                         # generate sequence from 01 to 20

chown
chgrp
chmod 640 file0[4-7]
chmod g+rx,g-w file1, file2

groupadd -g 5000 dev                              # works only after log out
usermod -G 5000 [student](student)                # works only after log out
gpasswd -M student,student1 dev                   # works only after log out
tail /etc/group

umask                                             # default permissions to all created files(/etc/profile) - reverse logic - what permissions not to set, and x is never set


strings /bin/ls                                   # print files printable symbols

/usr/lib/udev/rules.d/                            # udev default naming rules
/lib/udev/rules.d/                                # udev local naming rules

dd -if=/dev/sda of=/tmp/myMBR.bak bs=512 count=1  # backup MBR
dd if=/tmp/myMBR.bak of=/dev/sda                  # restore mbr record

ssh root@myHost
ssh -L 80:intra.example.com:80 gw.example.com     # local port forward
sshfs -o idmap=user user@serverHost: ~/myDirForFs # home dir(nothing after ':' to local ~/myDirForFs mapping
echo "ServerAliveInterval 60" >> ~/.ssh/config    # for staying connected and pinging every 60s
fusermount -u ~/myDirForFs                        # for unmouting sshfs

renice +1 <pid>
```

## Sbt

```
sbt "whatDependsOn com.adform.dp storm-commons-core" | less -R
sbt provided:dependencyBrowseGraph # not test only dependencyes and no provided ones
sbt test:dependencyBrowseGraph
sbt "inspect test:compile"
sbt "inspect tree" | less -R

sbt "~compile" # recompile on code change
```

## Zathura

```
:bmark <name>         " set or overwrite bookmark
:blist                " list bookmarks
:blist <bookmarkName> " go to specified bookmark
<tab>                 " table of content
```

