# Vim

## Autocompletion

* filename
* omni - similar to IntelliSense
* dictionary lookup
* generic keywords

## Spell Check

Vim out of the box supports regional variations of English.
```
:h spellang

:set spell
:set spellang=en_us
```
For specific professional jargon and terms separate files can be created
```
setlocal spelllang=en_us
setlocal spellfile=~/.vim/spell/en.utf-8.add
setlocal spellfile+=~/books/practical_vim/jargon.utf-8.add
```

## Mappings

`map/unmap`
`noremap` - no recursive mappings
`verbose map` - includes information where the key was defined

Some mappings can be overrode by plugins etc. `verbose map` will show files where mappings are defined.
In some cases plugins provide variables to enable/disable their mappings.
If key is defined correctly, but it still does nothing, it's possible that some app intercepts key before vim.
Next try could be `unmap/iunmap` - remove mapping and then add again

## Vim plugin creation

Plugin is nothing more than a vim script file that is loaded automatically.
It can be done by putting vim file into plugin dir.

Plugin types:
* Global - used for all files
  $VIMRUNTIME/plugin - user plugins
  $VIMRUNTIME/macros - plugins comming with vim
* Filetype plugin - used only for a specific type of file
  $VIMRUNTIME/ftplugin

File type plugins has special naming:
ftplugin/<filetype>.vim
ftplugin/<filetype>_<name>.vim
ftplugin/<filetype>/<name>.vim

Documentation can be added like `~/.local/share/nvim/site/doc/my-plugin/my-plugin-doc.txt`
`:helptags ~/.local/share/nvim/site/doc` - generate the local tags file 
`:help local-additions` - list added documentation files

### Functions

```
function s:Add(from, correct)
  let to = input("type the correction for " . a:from . ": ")
  exe ":iabbrev " . a:from . " " . to

endfunction
```

* `s:` - local function

`<SID>` - can be used with mappings
