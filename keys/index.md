# Key bindings

[i3](i3)
[bash](bash)
[Vimwiki](Vimwiki)
[Vim](Vim)
[Top](Top)
[atop](atop)
[glances](glances)
[scala](scala)
[vifm](vifm)
[tmux](tmux)
[kubernetes](kubernetes)
[blender](blender)
[promQL](promQL)
[vagrant](vagrant)
[aerospike](aerospike)
[profiling](profiling)
[mime](mime)
[intellij](intellij)

## Hotkeys

```
sudo showkey                      # print pressed key number
xmodmap                           # displays and edits keyboard modifier map
less /usr/include/X11/keysymdef.h # xorg key codes
less # shift+f follow current file
less # ctrl+c stop less following

!$ # last command last argument
!* # last command all args
```

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
journalctl -fe | grep servers
journalctl _COMM=<tab>
journalctl -o json-pretty # see journalctl field names
journalctl -t kernel # filter by SYSLOG_IDENTIFIER
journalctl -u sshd # filter by systemd unit
journalctl -p2 # show messages critical and worse
journalctl --list-boots
journalctl -S 01:00:00 -U 01:10:05 # show since until, can be with full dates
journalctl --since 2017-12-20 --until 2017-12-24
journalctl --since yesterday -u NetworkManager
journalctl -e --unit systemd-udevd
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
history 1 # show all history from first entry

rclone lsd remote: # list directories in top level
rclone ls gdrive: # list all the files in your drive
rclone copy /home/source remote:backup
rclone sync /tmp/backup gdrive:backup

tar -czvf <tarFile> <folder/fileToArchive>
tar -xvf <fileToExtract [<whereToExtract>]                           # extract archive to specific folder
xclip -sel clip id_rsa.pub                                          # copy file content to clipboard

ln -s <pathToFile> <pathToLink>                                     # create soft link

yay -Ql package_name                                             # list files belonging to package
yay -Qi                                                          # show installed packagies
yay -Qi package_name                                             # show package info including what depends on package and it's dependencies
yay -Qe                                                          # show only programs that you explicitly installed
yay -Qdt                                                         # orphan dependencies
yay -Qo file                                                     # find to which package file belongs
yay -Syyu --noconfirm --needed                                                        # download fresh copy of master package database and upgrade every package #maintenance
yay -Sii                                                         # rever dependencies #
yay -Si                                                          # dependencies of remote packages
yay -Sc                                                          # remove cache of old packages #maintenance
yay -U /var/cache/pacman/pkg/kdiff3-1.8.4-1-x86_64.pkg.tar.zst   # install old package version from file or downgrade package
yay -Rns <package_name>                                          # remove package with dependencies if they are not used elsewhere
yay -Rdd <package_name>                                          # remove package, ignoring it's dependencies
yay -Si xmonad                                                      # show extensive info about package
yay -Sua                                                            # update AUR packages
yay -Pu                                                             # give updatable packages
yay -Yc                                                             # removes uneeded dependencies #maintenance
yay -Ps                                                             # print package information summary #maintenance
yay -Syu                                                            # like pacman + updates AUR packages
yay -Qua # show what packages are installed and are updatable

yum list installed
yum install <pkg_name>

cat * | grep -v "^$"                                                # exclude lines which start with dollar sign
coproc (zathura "$booksFolder/$1 &)                                 # for running commmand as separate process

^x^e # edit current command line in default editor

echo "sth\nhello\n" | tr '\n' ' '                                   # translate(replace) all new lines with spaces
echo b{ed,olt,ar}                                                   # beds bolts bars
echo testfile{0,1,2,3,4}.txt                                        # testfile0.txt testfile1.txt...
echo test{0..20}{a..f}                                              # cycle in cyle
ls *e.?6?*.asc                                                      # file globbing
ls *[0-9][a-fgh][!m-o]*
ls | column
ls -t                                                               # sort by time
mv -t <dir> file1 file2 file4*.txt                                  # move multiple files
someArray=("my" "array" "values") # bash array
joinArray=("${arr1[@]}" "${arr2[@]}") # join two arrays
$((1+2)) # bash add integers

error.sh 1> capture.txt 2> error.txt # stdout to on file, stdin to other
error.sh > capture.txt 2>&1 # stderr & stdout to same file
error.sh 2>&1 # stderr to stdout
error.sh 1>&2 # stdout to stderr

grep -iRl "lenovo" ./ # find text in all files
find . -type f -empty ! -name "*test.file*"                         # ! inverts name filter
find / -type f -links 4                                             # find all files with 4 harldinks
find /usr -inum 531003                                              # find files with inode 531003
find /usr -samefile /usr/sbin/mkfs.ext3
find ./ -type f -exec sed -i 's/foo/bar/g' {} \;                    # replace in all files foo to bar
find . -type f -exec mv {} booksToReview \; # move files to folder
find . -printf "%T@ %Tc %p\n" | sort -n
find {$dir1,$dir2} -type f -exec grep -Iq . {} \; -print # read from multiple directories, filter out binary files

w                                                                   # show logged users and what are they doing
who                                                                 # shows currently logged users
whoami                                                              # current user
id # show user id
uptime
tty                                                                 # print device of terminal
/etc/passwd
/etc/shadow                                                         # passwd moved to shadow, it's safer as it can be read only by root
openssl passwd -6 mypassword
smbpasswd -r adform.com -U $AD_USERNAME_WITHOUT_@adform.com # change password
passwd someUser # change password for someUser

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

lscpu # get cpu info, cpu architecture etc
lsblk
df -h # show available space
du -sh * | sort -h
du -sh .[^.]* | sort -h # summarized sizes including hidden files
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
free -h
vmstat
iostat -j ID 

lshw # results can be questionable - inacurate or wrong because, because hardware vendors not always cooperates
hwinfo --short | less # hardware info
dmidecode -t 2                                                      # DMI(Desktop Managment Interface)system's hardware components description, uses SMBIOS info(data collection performed by BIOS)
lsusb -v | less
lsusb -t                                                            # tree
usb-devices                                                         # same as lsusb but more
lspci -v | less

xev # print contents of X events

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
usermod -G 5000 student                                  # works only after log out
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
dd if=/home/dago/Downloads/archlinux-2021.01.01-x86_64.iso of=/dev/sdb bs=512 status=progress # make bootable disk

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

curl wttr.in                                                        # get cool looking weather forecast in console
curl <someUrlWithJson> | jq '.' # get reformated json
cat joinBackup | jq '.partitionDelays | .. | .lastConsumedItemTime?' | sort
jq -s '.[0] as $a | .[1] as $b | $a * $b | .prices = $a.prices + $b.prices' product1.json product2.json | unique # join two different json files
jq -s 'reduce .[] as $item({}; . * $item)' prouct1.json prouct2.json
cat someXmlFile | xq # convert to json 

last                                                                # show a listing of last logged in users
lastb                                                               # all bad login attempts

sxiv -t *.jpg                                                       # thumbnail
ls *.jpg | sxiv -tio                                                # use it to select images and get selected imgs list
f # sxiv full screen
space # sxiv image forward
backspace # sxiv image backwards

xrdb -merge ~/.Xresources # load Xresources and merge with current
xrdb -query -all # see default settins for your X11 apps

scanimage --format=png --output-file Invoice_200_1.png --progress

scp /file/tosend username@remote:/where/to/put

ctrl+/ # get slack hotkeys
```

## Sbt

```
sbt help # get help
sbt help <command> # get help on <command>
sbt !: # get command history

sbt project[s]
sbt tasks [-v[v]]|[-V] # list tasks
sbt settings # list settings
sbt show <setting/task name> # show setting value/run task and see return value

sbt project <projectId> # set this project to different one

sbt package # creates jar
sbt dist # creates zip
sbt Docker/publishLocal # publish application in docker, then docker run <imageName>

sbt "whatDependsOn com.adform.dp storm-commons-core" | less -R
sbt provided:dependencyBrowseGraph # not test only dependencyes and no provided ones
sbt test:dependencyBrowseGraph
sbt "inspect test:compile"
sbt "inspect tree" | less -R

sbt "~compile" # recompile on code change
sbt "show fullResolvers" # show all resolvers of project

sbt "runMain org.may.path"
sbt "inspect tree dist"

sbt ";reload plugins"
sbt dependecyUpdates # get possible updates for project
sbt "reload plugins; dependencyUpdates" # get possible plugin updates

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
git add -a -m "commit msg"       # add all and commit
git checkout -b "new branch name"
git push origin branchName
git reset                        # unstage all staged files
git add ^t                       # fzf autocomplete
git restore <file>...            # restore/undo changes in file
git merge master
git describe --tags
git push origin --tags           # push all tags to origin
git push origin v1.5             # push only specified tag to origin
git tag -d <tagName> # delete local tag
git push --delete origin <tagName> # delete tag
git fetch --all
git commit -m "retrigger checks" --allow-empty
git update-index --chmod=+x myExecutableFile # set execution rights in git
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
host 

iptraf-ng # traffic monitor and more, GUI program analog - wireshark
/etc/sysconfig/network-scripts
nmcli
nmcli connection add save yes type ethernet ifname enp0s3 con-name enp0s3 ip4 10.0.2.11/24 gw4 10.0.2.1 ipv4.dns "10.0.2.1 8.8.8.8" # setting static ip

firewall-cmd --list-ports [--permanent]                             # list existing rules, permanent show rules that will be active after restart
firewall-cmd --add-service=telnet
firewall-cmd --remove-service=telnet
firewall-cmd --list-services
firewall-cmd --list-services [--permanent]
firewall-cmd --runtime-to-permanent                                 # save all configuration

iptables-save                                                       # list rules
iptables -I INPUT 5 -p tcp -m state --state NEW -m tcp --dport 23 -j ACCEPT; iptables-save

```

## Tmux

```
Ctrl-B : setw synchronize-panes on
Ctrl-B " Split horizontally
Ctrl-B % Split vertically
Ctrl-B <arrow> move through panes
```

## Snippets

```
scriptName=$(basename $0)
die() { echo >&2 "$@" ; exit 1 ; }

confirm() {
    # call with a prompt string or use a default
    read -r -p "${1:-Are you sure? [y/N]} " response
    case "$response" in
        [yY][eE][sS]|[yY]) 
            true
            ;;
        *)
            false
            ;;
    esac
}
```


