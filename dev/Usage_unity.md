# Usage Unity

Many same tasks are executed in different environments, so hotkey problem exist with possibility to unify

## Environments

* i3 windows manager
* Shell(zsh and possibly more)
* nvim

## Tasks

* Search
	* Files by name
		* Code file
		* Configuration file
		* Information file
	* Text in files
		* Text in code
		* Text in configuration
		* Text in information file
	* Server
* Navigate
	* To file
		* Code file
		* Configuration file
		* Book
	* To server
	* To program
	* To window
		* i3 window
		* vim window
	* List
		* Quickfix
* 

## Possibly combinable

* search
	* history
		* zsh & fzf - <C-R> 
		* vim & fzf - :History: 
	* files
		* zsh <C-t> (paste path to zle)
		* zsh >vf (open with $EDITOR)
		* vim <leader>n (open file)
	* words
		* vim & Grepper - search word under select/word with command
		* vim & fzf & grepper
		* vim & simple search in file `\`
			* <shift+/> for search? or <leader>
			* <shift+[n,N]> next, previous for quickfix or <leader>
		* zsh & grep

## Combined action

* rofi
	* ssh
	* programs
	* sh code examples
	* books
* vim like
	* text
	* shell cmd
	* file manager
	* browser
