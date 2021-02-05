Profiling

# VisualVM

## JMX

Set settings for remote app
```
-Dcom.sun.management.jmxremote.port=3333 \
  -Dcom.sun.management.jmxremote.local.only=false \
  -Dcom.sun.management.jmxremote.authenticate=false \
  -Dcom.sun.management.jmxremote.ssl=false \
```

```
-Dcom.sun.management.jmxremote.port=3333 -Dcom.sun.management.jmxremote.local.only=false -Dcom.sun.management.jmxremote.authenticate=false -Dcom.sun.management.jmxremote.ssl=false
```


# Linux application profiling

## Pef_events (aka "perf", aka PCl - Performance Counter for Linux) 
http://www.brendangregg.com/perf.html

```
# needs to run with root/sudo

perf list # listing all currently known events
perf list 'sched:*'

perf record -F 99 -ag -- sleep 30 # creates perf.data file
perf record -F 99 -p <PID>
perf record -e block:block_rq_issue -ag # tracing I/O, stop Ctrl+C

perf stat ls # get statistics on ls command
perf stat -e cs # get statistics on context switches

perf trace ls # trace 

perf report # show perf.data in an ncurses browser (TUI) if possible
perf script # list all events from perf.data
perf annotate --stdio # disassemble and annotate instructions with percentages

# common options
# -a all cpus
# -e <event> list of syscalls and other perf events
# -p pid
# -t tid
# -g enables stack traces, mandatory for flame graphs
```


Standard linux profiler, can sample stacks of (almost) everything on CPU
Many event sources
* Timer-based sampling
* Hardware events
* Tracepoints
* Dynamic tracing


### Requirements

* Linux
* Oracle/OpenJdk(1.8u60+) + latest Zing
* -XX:+PreserveFramePointer -> Walk the stack
* Recommended for extra precision for inlined methods
	* -XX:+UnlockDiagnosticVMOptions
	* -XX:+DebugNonSafepoints
* Need permissions/some Linux fu 
* Need perf-map-agent (build your own)
* perf

## ftrace
