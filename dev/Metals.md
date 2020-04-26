# Metals

## Dependencies

* NVim
* Coc LSP client plugin
* Metals language server plugin

## Installation

* `init.vim` configuration
* Setup Java (install node find-java-home, coc uses it to find java)
* 

### Debugging

`tail -f .metals/metals.log` - for seeing import progress
`:Coclst diagnostics` - list all compile time errors
`<space>t` - Tree View Protocol, `r` triggers compilation
