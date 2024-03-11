# GDB Debugging

* `tui enable` enables the text-user-interface mode where you can see in with a split-window the current code location
    * `focus cmd` to make arrows keys work normally in tui mode
    * ctrl+l if tui mode messes up

* tab autocomplete to find options
  
* breakpoints
  
  * `tbreak`: temporary break
    
  * `rbreak`: match regular expression to break point locations and add for all of them
    
* `crtl+x+2`: second window; cycle through
  
* `ignore <breakpoint number> <occurunces>` to skip over a breakpoint a certain number of times -> very useful if determinsitic program fails after a certain number of times
  
  * Couple this with `ignore <breakpoint number> 99999999` and after completion/crash use `info break` to find number of times breakpoint was hit
    
  * To avoid arbitrary big number add `continue` to `commands <breakpoint number>`
    
* `cond <breakpoint number> <condition>` to make breakpoint conditional
  
* `break foo if bar > 10`: create new conditional break point
  
* `break foo thread 3`: stop at foo only in thread 3
  
* `watch foo`: stop when foo is modified
  
  * Can be conditions etc. like above
* `watch -l` evaluates once and then watches the resultant memory location, NOT the reevaluation of the expression
  
* `rwatch` is NOT regex watchpoint, but weatch point for reads to things
  
  * `awatch` is access watchpoint (read or write, but value might not change for example)
* Backtrace (`bt`) is useful, but doesn't go *back in time*
  
  * `record`
    
  * `reverse-stepi`
    
  * `reverse-continue` (e.g. to a watch point)
    
  * N.B hardware watchpoints don't work with stack pointer (`set can-use-hw-watchpionts 0` to force software watch point)
    
    * Hardware watch points uses special registers (use too many and you will get an unexplained crash (normally 4))
      
    * Software watch point evaluates after every step. This incurs a heavy context switching performance penalty
      
      * Can alleviate this by making sure it is run locally etc. if on a remote machine
* `whatis` tells you type information
  
* Catchpoints also exist!
  
  * `catch catch` to stop when C++ exceptions are caught
    
  * `catch syscall nanosleep` to stop at nanosleep system call
    
  * `catch syscall 100` to stop at system call number 100
    
* You can `call` functions too e.g. `call foo()`
  
  * Be aware that this is what happens if you do `print foo()` too
* `dprintf foo.c:10, "bar is %d\n", bar` allows you to dynamically add prints without recompiling! At least do this if you have to do printf debugging!
  
  * `set dprintf-style gdb|call|agent`
    
  * `set dprintf-function fprintf`
    
  * `set dprintf-channel mylog`
    
* `skip` functions/libraries that your don't care about or trust
  
  * e.g. `skip -rfu ^std::.*` will skip stepping into all code in the std namespace
    
  * This can get a little unintutive if you use things such as callbacks or step out of a function into skipped code etc.
    
* `compile code` - compile code typed at console and run it
  
* `compile file` compile source code from a file and run it
  
* `compile print` use compiler to evaluate an expression, print result
  
  * All can inject into the program and is very powerful. You can combine this with gdb scripting (`cat <flie.gdb> && cat > gdb ...`)
* You can run commands on gdb startup by using a dotfile: `~/.gdbinit`
  
* Compile with `-g 3` or later etc. to get better debug info (to stop "value optimised out" etc.)

## Docker compatibility

To be able to use `gdb` in a docker container, you need to run the container with additional arguments.

```bash
docker run --cap-add=SYS_PTRACE --security-opt seccomp=unconfined ...
```

If you are using docker-compose, this can be specified like so:

```yaml
security_opt:
    - seccomp:unconfined
cap_add:
    - SYS_PTRACE
```
