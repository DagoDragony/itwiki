# Troubleshooting

## Shell

* Fail to use $ before variable
* if conditions spacing is very importat `[[ $sth="..." ]]`. Miss a space and it will fail..
* Braces creates separate context and it will eat "exit 1" without exiting script
  `.. && {echo "bla"; exit 1}` good
  `.. && (echo "bla"; exit 1)` bad (doesn't exit script)
* good use of > /dev/tty when you want to call and editor in pipeline e.g. with xargs
