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

Standard linux profiler, can sample stacks of (almost) everything on CPU
Many event sources
* Timer-based sampling
* Hardware events
* Tracepoints
* Dynamic tracing
