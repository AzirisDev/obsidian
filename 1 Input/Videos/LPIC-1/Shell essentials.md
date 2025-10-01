Shell is a place where you run commands and see the output. We can work with shell by launching terminal.

We have many shells like bash(the popular one), zsh, dash, ksh, csh. You can check which shell you are running using `echo $0` or `echo $SHELL`

When processing commands, it first checks whether it is internal or external command: internal will execute immediately; external will have `PATH` environment variable where we have linux executable file to run it.

#### Essential commands
- type `command` - shows internal/external command
- which `command` - path to command
- whatis `command` - short description
- whereis `command` - locates file, manual page files etc
- uname -a - system information
- * - list of all files
- \ - escaping

#### Environment variables
[[Environment variables]]

#### Type of shells

- login & interactive shell - when you login to the terminal
- non-login & interactive shell - when you open another shell within the shell
- non-interactive shell - when you just run the command or script


Links:

202509111235

