# Vim

## Autocompletion

* filename
* omni - similar to IntelliSense
* dictionary lookup
* generic keywords

## Mappings

`map/unmap`
`noremap` - no recursive mappings
`verbose map` - includes information where the key was defined

Some mappings can be overrode by plugins etc. `verbose map` will show files where mappings are defined.
In some cases plugins provide variables to enable/disable their mappings.
If key is defined correctly, but it still does nothing, it's possible that some app intercepts key before vim.
Next try could be `unmap/iunmap` - remove mapping and then add again
