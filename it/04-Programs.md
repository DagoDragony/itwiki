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

## Tsp

Task spooler

```
tsp echo hello # registers task for echo hello command
tsp # lists all jobs
tsp -c <jobId> # lists output of tsp job with id jobId
tsp -C # clear finished jobs
```

Examples
```
tsp echo hello # for simple statement
tsp sh -c 'notify-send "tsp test"' # more complicated scripts should run like sh -c or similar
```

### Multiple queue lists

Give environment variable any path and run command(each time with TS_SOCKET defined).
This way it will create separate task list, which you can see when TS_SOCKET is specified.
Default `TS_SOCKET` is $TMPDIR/socket-ts.[uid]
```
TS_SOCKET=/tmp/shorttask/ tsp echo A
TS_SOCKET=/tmp/shorttask/ tsp echo B
TS_SOCKET=/tmp/shorttask/ tsp echo C

TS_SOCKET=/tmp/shorttask/ tsp # list that we created
tsp # default list
```

## Vim keys

`map/unmap`
`noremap` - no recursive mappings
`verbose map` - includes information where the key was defined

