
Processes can be observed with the command `ps`

`ps -aux` :
-  `a` for processes froom all usrs
- `u` for formatting
- `x` processes not attached to a terminal (background)
- 


Each process is associated with its own ID (PID), which can be used by other command:
- `lsof -p <PID>`: show information about process (lsof = list open files)
Other lsof options:
- -i: network connections
- -P: display port numbers
- -n: not DNS resolving

Other useful tool: `osquery`

#### Get current process

If inside a program, can get current process command line with: 
`/proc/self/cmdline`