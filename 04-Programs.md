# [Programs](Programs)

## Cronie

```
sudo pacman -S cronie
crontab -l # list crontabs
crontab -ie # edit crontabs(interactive)
crontab -r # remove crontabs
```

```
# mm  hh  DD  MM  W /path/progam [--option]...  ( W = weekday: 0-6 [Sun=0] )
  21  01  *   *   * /usr/bin/systemctl hibernate
  @weekly           $HOME/.local/bin/trash-empty
  01 * * * * /bin/echo Hello, world! # runs every hour on first minute
  * * * * * notify-send "Test every minute" "$(date)"
  * * * * *  XDG_RUNTIME_DIR=/run/user/$(id -u) notify-send Hey "this is dog!"
```


for testing part:
`run-parts -v /etc/cron.hourly` - run jobs manually
`cronnext -cl` - print jobs and when next run will be
