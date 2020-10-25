tmux

```
tmux new-session
tmux new [-ssomeSessionName] [-ntopwindow name] -- shell cmnds # create new session with name mysession

C-b ? # hotkeys
C-b / <someKey> # specific hotkey description

C-b :
tmux new -Asmysession # attach to session
C-b w # select window
C-b s # info about sessions

C-b c # new window
new-window
neww
C-b [0-9]
C-b '

tmux ls # list windows
tmux attach # attaches to most recent session
tmux attach -tmyssession

C-b % # splits into to horizontal panels
C-b " # splits vertically

:setw synchronise-panes # apply to all group

:kill-server

```
