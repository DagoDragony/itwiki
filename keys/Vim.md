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
vip     " select inner paragraph
vipga = " mark current paragraph and align by =
gaip  = " align inner pagragraph by =
```

## Windows

```
<C>ww        " move to next vim window
:sp [<file>] " horizontal split
:vs [<file>] " vertical split
```

## Vim Ide

```
<leader>rn - rename
gd - <Plug>(coc-definition)
gy - <Plug>(coc-type-definition)
gi - <Plug>(coc-implementation)
gr - <Plug>(coc-references)
<space>a - :CocList diagnostics
<space>c - :CocCommand - list commands
	metals.doctor-run checks if everything is compatible
	TVP console - shows statuses of compilation etc
<C-o> - previous cursor location
<C-i> - forward to previous cursor position

<leader>Shift* "
<leader>* " search for current word in files
nmap gs " search for current selection

gcc - to comment out line
gc - comment out target of motion
gcap - comment out a paragraph
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
cs"'      " change surounding " with '
ds"       " remove surounding "
<leader>f " Goyo toggle
```

