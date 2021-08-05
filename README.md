# ikhane-dbg
*im depressed*
## random shit: data sources
`/proc`, `procfs`: hierarchy of pseudo-files with access to each process memory, resource utilization, thread list, exec path.. *`/proc/[pid]/mem` provides direct access to a process' memory* | *`/proc/[pid]/exe` is a symbolic link to the path of the executable, I could call `open` on it to get debug info* | *`/proc/[pid]/maps` provides description for each region of mem mapped into the process: address range, permission bits, the file backing the mem region, this is used when a process is linked to **shared libraries***

## random shit: debug information
The main task is to translate raw memory locations into program objects like *functions, variables, types..* For that, using the following debug info *nlah nlah, I'm lost*:

 * location of program functions and global variables
 * stack layout of each function, dependant on the current location of execution within a func *(instruction pointer)*
    * expressions that evaluate as the locations of local vars and params on eavh func's stack
  * types of vars, which combines with the above debug info, indicate the mem range in which to look for and read a particular var

## just shit: debugging flow of things I guess I should die
 1. identify process to debug: `pid`, *can be retrieved using `pgrep pattern`*
 2. **ATTACH AND STOP**: pause process execution to extract data from it
    * using the `ptrace()`:
      * `PTRACE_ATTACH`: establish tracer-tracee relationship, and more.*(stops target process, allows debugger to read from process mem and registers)*
      * `PTRACE_DETACH`: reverses attech effects and allows process to continue its execution
