# Key bindings

[Vimwiki](Vimwiki)
[Vim ide](Vim-ide)

# fzf

```
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
print -z "stsdth # puts argument onto the editing buffer stack
```

# vim

```
:s/^/#    " comment
:s/^#/    " uncomment
<<        " unindent
>>        " indent
<leader>n " fzf open file
<C-p>     " NERDTreeToggle
<F3>      " NERDTreeToggle
cs"'      " change surounding " with '
ds"       " remove surounding "
<leader>f " Goyo toggle
```

# various

```
tar -xvf <fileToExtract <whereToExtract> # extract archive to specific folder
xclip -sel clip id_rsa.pub               # copy file content to clipboard

pacman -Ql package_name " list files belonging to package
pacman -Syu             " download fresh copy of master package database and upgrade every package
pacman -u file.tar.gz   " install from package
pacman -Qo file         " find to which package file belongs

cat * | grep -v "^$" | grep -v "^\`" | grep -v "^#" | grep -v "^\["
```

# snippets

```
cbl   " code block
ilc   " inline cod
*     " italic
**    " block
sec   " h1 header
ssec  " h2 header
sssec " h3 header
<C-R> " finish with snippet editing
```

# sbt

`sbt "whatDependsOn com.adform.dp storm-commons-core" | less -R`
