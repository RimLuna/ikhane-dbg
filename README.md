# ikhane-dbg
*im depressed*
## random shit: data sources
`/proc`, `procfs`: hierarchy of pseudo-files with access to each process memory, resource utilization, thread list, exec path.. *`/proc/[pid]/mem` provides direct access to a process' memory* | *`/proc/[pid]/exe` is a symbolic link to the path of the executable, I could call `open` on it to get debug info* | *`/proc/[pid]/maps` provides description for each region of mem mapped into the process: address range, permission bits, the file backing the mem region, this is used when a process is linked to **shared libraries***



