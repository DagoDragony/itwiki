# Key bindings

[Vimwiki](Vimwiki)
[Vim](Vim)

## Fzf

```
type for               # check what type is keyword
`whence -wm '*'`       # shows what shell knows - commands, functions, reserved words..

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

w                                        # show logged users and what are they doing
who                                      #
whoami # current user
id
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

