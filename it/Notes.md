# Notes

## Git


aliases
forgit and fzf
try diff-so-fancy

## Desktop files

dir `~/.local/share/application`
eg.
```
[Desktop Entry]
type=Application
Name=Torrent
Exec=/usr/bin/env transadd %U
```

for the default applications set new *.desktop file to mimeapps.list
`~/.config/mimeapps.list`

```
[Default Applications]
x-scheme-handler/magnet=torrent.desktop;
application/x-bittorrent=torrent.desktop;
```

`xdg-mime query default image/png`

`/usr/share/mime`

## Snippets UltiSnips

Vimwiki sets for markdown file type of vimwiki, so other plugins don't recognise file as markdown
and snippets are not loaded

`:set filetype?` - get filetype
Settings needed to recognise filetype
`filetype on`
`filetype plugin on`
`filetype indent on`
`:filetype` - to check file type recognision settings



