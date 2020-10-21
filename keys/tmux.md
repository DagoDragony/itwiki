tmux

```
tmux new-session
tmux new [-ssomeSessionName] [-ntopwindow name] -- shell cmnds # create new session with name mysession

C-b ? # hotkeys
C-b / <someKey> # specific hotkey description

C-b :
tmux new -Asmysession # attach to session

C-b c # new window
new-window
neww

tmux ls # list windows
tmux attach # attaches to most recent session
tmux attach -tmyssession


:kill-server

```

