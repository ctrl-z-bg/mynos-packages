# sysmonitor

The system at work, in a window, updated once a second:

- the processor's load and the memory in use, each with a graph of its
  last two minutes;
- the file systems, `/` (the RAM disk), `/tmp` and `/disk`: used and
  total space;
- a table of the processes: pid, name, CPU (% of the processor in the
  last second), memory (its pages in memory, the RAM disk's apart),
  threads, page faults a second, and the services it serves. A click on
  a column's title sorts by it (CPU, memory, pid, name, faults).

A click on a row selects a process; **End process**, clicked twice,
ends it (as `kill`: not a driver, unless sysmonitor could start one).
Ending a service is allowed and shown: `init` starts it again.

The numbers are the kernel's, through system call 38
(`Mynos.process_stats`): CPU time in ticks of 10 ms, memory in pages of
4 KB, page faults as `ps -f` counts them. A MyNOS older than
2026-11-23 does not have that call: sysmonitor then says so.

Start it from the menu's Applications, or with `sysmonitor &` in a
Terminal.
