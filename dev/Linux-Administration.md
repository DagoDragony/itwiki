# Linux Administration

## CPU

`top`
* us - user space cpu time spend
* sy - system cpu time spend(mostly kernel tasks as memory management, task dispatching)
* ni - "nice" time. Positive nice time cpu spend
* id - idle time cpu spend(not performing any processing or waiting for I/O)
* wa - cpu waiting on I/O operations
* hi - cpu time waiting for hardware interrupts - a high number especially when wa is also high 
  can indicate  that hardware speed is too slow for the existing load
* si - number of system interrupts during the time interval - a high number of software interrups
  especially when w is also high can indicate that some apps may be in some sort of tight loop
  or race condition
* st - time stolen from "this" VM because it can run, but another VM is running and VM hypervisor
  cannot allocate time to "this" VM. This should always be zero for a non-virtual host. In a virtual
  host a number significantly greater than zero might mean that more physical CPU power is required
  for the given real and virtual system load

these should always add up to rounding error 

The 0 is highest priority
PR=[0;99 real-time priority  100;139 - meant for user-space]
NI - nice [-20;+19] suggests kernel different priority. Lower value - higher priority
PR = 20 + NI

### Memory
 
* RES(RSS - Resident Set Size ) - shows how much RAM is allocated to that process
  Does not include swapped out memory
  Include memory from share libraries
  Include stack and heap memory
* VIRT(VSZ - Virtual Memory Size) - includes all memory that the process can access
  Including swapped out
  Including allocated but not used memory
  Including shared libraries memory
* SHR(Shared Virtual Memory) - it can be used for interprocess communications, but a more
  common scenario is that this is memory used by shared libraries that an application has linked in
  

### Things To Look For

* 0% idle time for extended periods - load averages could help to determine of whether system is
  overloaded or just very busy
* See there is no swap and that it's plenty of RAM left to use

## Interprocess communication

Pipe
```
# in console1
mkfifo mypipe

# in console2
lsblk -i > mypipe
# in stops until it is read

# in console1
cat mypipe
# console 2 releases command
```

## Processes

CFS (Completeley Fair Scheduler) - determines which processor gets CPU time

## Various

Internal commands
* is a part of a shell
* doesn't create separate process

External commands
* are loaded only when needed
* creates separate process on execution
