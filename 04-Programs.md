# [Programs](Programs)

sudo pacman -S cronie
crontab -l # list crontabs
crontab -e # edit crontabs
crontab -r # remove crontabs

01 * * * * /bin/echo Hello, world!

# mm  hh  DD  MM  W /path/progam [--option]...  ( W = weekday: 0-6 [Sun=0] )
  21  01  *   *   * /usr/bin/systemctl hibernate
  @weekly           $HOME/.local/bin/trash-empty
