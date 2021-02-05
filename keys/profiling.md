profiling

```
perf record -F 99 -ag -- sleep 60
perf script | ./stackcollapse-perf.pl | ./flamegraph.pl > perf.svg
```

