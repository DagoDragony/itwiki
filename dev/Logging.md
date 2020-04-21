# Logging

## Common

Categories/Loggers - for disabling enabling logging requests
* com.foo
* com.foo.bar
* etc

Priorities/levels
* Error
* Warn
* Infor
* etc.

Appenders/handlers - for multiple output destinations
* Console
* Files
* GUI components
* remote socket servers
* remote UNIX syslog daemons
* NT event loggers

Layouts

## `slf4j` (Simple Logging Facade for Java)

A simple facade or abstraction for various logging frameworks(e.g. java.util.logging, logback, log4j)
allowing the end user to plug in the desired logging framework at deployment time.

There are various messes with this. There exists libs like
* `log4j-over-slf4j` - for easy migration from log4j it has **minimized** log4j lib that replaces previous log4j
  missing logger.setLevel(...), probably missing all methods that are not in `slf4j`
* `log4j-to-slf4j` - for easy migration from log4j 2 to be routed to `slf4j`
* `slf4j-log4j` - various `slf4j` libs with some lib underneath(you still need to update all parts with `slf4j` logger),
  there is multiple possibilities what can be underneath `slf4j`

## Loggers

* Log4J2
* Logback
* Log4J (deprected)
* JUL(Jdk Logger, Java.util.logging) - simplistic, lacks performance and features


# Questions

* xml or programmatic? When?
* how to override only small part of xml?
* all possible options of lib easy review?
* categories, appenders, layouts
