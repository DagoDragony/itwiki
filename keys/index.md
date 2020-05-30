# Key bindings

[Vimwiki](Vimwiki)
[Vim](Vim)

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
man systemd.journal-fields # fields to match by
systemctl list-units       # list units that systemd currently has in memory
systemctl list-unit-files  # see which are enabled
systemctl status           # shows tree overview
systemctl --failed         # shows system status, like degraded

ls -al /lib/systemd/system/runlevel*
systemctl get-default
```



## Various

```
tar -xvf <fileToExtract <whereToExtract> # extract archive to specific folder
xclip -sel clip id_rsa.pub               # copy file content to clipboard

pacman -Ql package_name                  # list files belonging to package
pacman -Syu                              # download fresh copy of master package database and upgrade every package
pacman -u file.tar.gz                    # install from package
pacman -Qo file                          # find to which package file belongs
pacman -Rdd <package_name>               # remove package, ignoring it's dependencies
pacman -Sii                              # rever dependencies #
pacman -Si                               # dependencies of remote packages
pacman -Qi                               # show installed packagies

cat * | grep -v "^$"                     # exclude lines which start with dollar sign
coproc (zathura "$booksFolder/$1 &)      # for running commmand as separate process

echo "sth\nhello\n" | tr '\n' ' '        # translate(replace) all new lines with spaces
echo b{ed,olt,ar}                        # beds bolts bars
echo testfile{0,1,2,3,4}.txt             # testfile0.txt testfile1.txt...
echo test{0..20}{a..f} # cycle in cyle
ls *e.?6?*.asc # file globbing
ls *[0-9][a-fgh][!m-o]*

find . -type f -empty ! -name "*test.file*" # ! inverts name filter

w                                        # show logged users and what are they doing
who                                      #
whoami                                   # current user
id
tty                                      # print device of terminal

lscpu
lsblk
df -h
dmesg                                    # print or control kernel ring buffer


stat <fileName>                          # statistics about file - times, size, inode..
cal                                      # calendar for this month

info coreutils                           # gnu core utils
yes stringThatWouldConstantlyRepeat      # infinite stream - could be used for maxing out file
dd if=/dev/sdb1 bs=512 count=1           # print to console first 512 bytes (could be used to read write MBR)
cat /dev/urandom                         # infinite stream of random symbols, could be used to overwrite data to be unrecoverable
shred                                    # for overwriting individual files, partitions, drives
od -c -N 1000 < /dev/urandom             # octal display
fc                                       # open last command in editor

pacman -Sq [<groupName>]                 # remote groups of software

top
atop
htop
iotop
free
vmstat
iostat -j ID 
lsusb -v | less
lspci -v | less

                                         # results can be questionable - inacurate or wrong because, because hardware vendors not always cooperates
lshw
dmidecode -t 2

sensors                                  # temperature sensors
sensors-detect

smartctl -x /dev/nvme0n1
hddtemp

sar                                      # system activity reporter

shopt                                    # bash options

grub-install --version
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

