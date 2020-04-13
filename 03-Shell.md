[#](#) Zsh

You can get whole list of keywords with type
`whence -wm '*'`(shows what shell knows - commands, functions, reserved words..)

## Builtins

trap, limit/unlimit

### vared

Lets edit variables in line
```
array=('one' 'two' 'three')
vared array
```

## Commands

`which -a ls` - shows ls path and that ls actually is alias

## Functions

### Widgets
Function that can be binded to keys
```
fzf_srch_history() {
	command echo $(history)
}
zle -N fzf_search_history fzf_srch_history


accept-line() {
	print -n "\e]2;Executing $BUFFER\a"
	zle .accept-line
}
zle -N accept-line
```

`zle -lL` - list all widgets
	  
	  
* 


* options - all boolean, each describs on particular shell behaviour
	* modified with setopt(same as set -o) and unsetopt 
	* checked with `[[ -o rcs ]]`, echo $options[rcs]
* variables
	* putting $ before variable is called parameter expansion(sometimes called substitution)
* modifiers `:h`, `:t` etc more 'man zshexpn' modifiers section.
* Prompts
	* `$PS1` - default interactive shell prompt 
	* `$PS2` - is shown when the shell is waiting for some more input
	* `$PS3` - is shown within a loop started by the shell's select mechanism
	* `$PS4` - usefull for debugging: there is an option XTRACE which causes the shell to print out lines about to be executed, preceded by $PS4
* Aliases alias foo='print I said foo'
* Environment variables `export VARNAME='value'`
* Keymaps
	* `bindkey -l` list exinsting keymap names
	* `bindkey -M <keymap>` list show bindings in keymap
* interactive shell
* login shell

File descriptors
* >&2
* 2>&1
* 3>&1
* >> - append to file
* > - overwrite the file
* |& - 

## Substitutions

### Modifiers
:h
:t
```
$#foo - foo string length
% foo=/usr/bin/cat
% print ${foo:h}
/usr/bin
% print ${foo:t}
cat
% print /usr/bin/cat(:t)
cat 
```
string substitution
```
% array=('a bar of chocolate' 'a bar of barflies' 
  array> 'a barrier of barns')
  % print ${array:s/bar/car/}
  a car of chocolate a car of barflies a carrier of barns
```

### Conditional substitutions

* print ${foo-bar} - use foo value if foo is set or use "bar"
* print ${foo:-bar} - use foo value if it's non zero string, else "bar"
* print ${foo:=bar} - use foo, but if it's not set before using set it to "bar"
* print ${foo:+bar} - if foo is set use bar, else use foo value abscense
* print ${@:?some message like missing file name} - if param not set print the message and exit shell

### Process substitutions

### Parameter substitution

```
% array=(one two three four)
% print ${array}
one two three four
% print ${array[3]}
three
% print ${array[2,-1]}
two three four

% array=(one two three four)
% print $#array
4

% array=(se vuol ballare signor contino)
% print ${array[(r)s*]} # search: r - first match from left, R - first from rigth
se

% array=(se vuol venire nella mia scuola)
% print ${array[(i)v*]} # get index: i from left, I from right
2

```


## Flags

### Padding

```
foo='abcdefghij'
for (( i = 1; i <= 10; i++ )); do
 goo=${foo[1,$i]}
 print ${(l:10::X::Y:)goo} ${(r:10::X::Y:)goo}
done
```

```
foo=one && print ${(r:l:10::X::Y:)foo}
XXXXXXYone
```

Bang history - !! returns last command
typset var='value in function' - after function restores var value or removes it if the wasn't any before
read someParam



# testing

* times
* 


# Questions

* Builtin documentations? 

