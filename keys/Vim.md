# Vim

## snippets

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

## recipies

```
vip         " select inner paragraph
viw         " select word
vipga =     " mark current paragraph and align by =
gaip  =     " align inner pagragraph by =
.,+3s/^.//g " substitute 3 lines forward - first match
.,$s/^.//g  " substitute till the end
%s/a/b/g    " substitute all lines
1,10s/a/b/g " substitute 1 to 10 line
```

## Windows

```
<C>ww        " move to next vim window
:sp [<file>] " horizontal split
:vs [<file>] " vertical split
```

## Vim Ide

```
<leader>rn     " rename
gd             " <Plug>(coc-definition)
gy             " <Plug>(coc-type-definition)
gi             " <Plug>(coc-implementation)
gr             " <Plug>(coc-references)
<space>a       " :CocList diagnostics
<space>c       " :CocCommand - list commands
<C-o>          " previous cursor location
<C-i>          " forward to previous cursor position

<leader>Shift* "
<leader>*      " search for current word in files
nmap gs        " search for current selection

gcc            " to comment out line
gc             " comment out target of motion
gcap           " comment out a paragraph

<space>a       " list all compilation errors
<leader>ws     " see expanded text of the line
@:             " repeat last command (useful after Rg <search>

/<C-r>=&include " show include pattern for current context search
:set suffixesadd? " extension that is added to autosearch import
:set includeexpr? " multiple paths to match possible search places
:ij " include search based jump
:checkpath! " all imported files

# Nerdree
mc " copy file under cursor
F2 " toogle

# Netrw
:Explore " netwr
:Sexplore "
:Vexplore "
F1 " help
<c-l> " refresh
<c-tab> " shring expand  a netrw/explore window
i - listing toogle
gn - make selected dir top of a tree
D - delete files or directories
mf - mark file
mF - unmark file
mu - unmark all files
md - apply diff to marked files
o - open directory in seperate window
p - preview window
mb - bookmark current dir
gb - go to prieviously bookmark dir
qb - list bookmarked directories and history
qf - display information on file
R - rename file or directory
x - view file with associated program
d - make directory
% - create and open a new file in netrw current dir
mz - compress/decompress
```

## Vimdiff

```
]c " next diff
[c " previous diff
do " diff obtain
dp " diff put
zo " open folded text
zc " close folded text
:diffupdate - re-scan the files for differences
```


## Autocompletion

```
<C-n>      " triggers generic autocomplete or next in autocomplete
<C-p>      " triggers generic autocomplete or next in autocomplete
<C-y>      " accept selected autocomplete
<C-e>      " dismiss selection and restore to previous

<C-x><C-f> " file autocompletion (fzf)
<C-x><C-s> " trigger spell autocompletion
```

## Spell Check

```
]s  " jump forward
[s  " jump backward
z=  " list suggested corrections
zg  " add current word to spell file
1zg " add to first spell file
2zg " add to second spell file(like professional jargon and similar)
zw  " remove current word from spell file
zug " revert zg or zw command for current word
```

## Various

```
:s/^/#    " comment
:s/^#/    " uncomment
<<        " unindent
>>        " indent
<leader>n " fzf open file
<C-p>     " NERDTreeToggle
<F3>      " NERDTreeToggle
cs        " '      " change surounding " with '
ds        " " remove surounding "
<leader>f " Goyo toggle
<Ctrl+r>  " redo
shift-tab " fzf select multiple files
:set list " show invisible symbols
:<C-f>    " open command line search and run with edit
```


