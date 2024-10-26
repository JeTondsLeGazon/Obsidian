
Stabilize shell with:
- On victim's machine: `python3 -c "import pty; pty.spawn('/bin/bash')"`
- CTRL+Z to put it in background
- Then on own machine: `stty raw -echo; fg`
- On victim's machine: `export TERM=xterm`