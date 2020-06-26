# Linux Install Automation

Save current state of installed packages and restore
```
yay -Qqe > packages.txt
yay -S --needed - < packages.txt # install all packages
```
