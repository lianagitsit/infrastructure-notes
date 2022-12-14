# Working with Commands

Commands can be one of four things:
1. An executable program 
2. A command built into the shell itself (e.g. `cd`)
3. A shell function 
4. An alias

## Identifying commands

It's sometimes useful to identify which of the four types of commands is being used. Some ways to find out:

`type` displays a command's type
- a shell builtin

`type *command*`

`which` displays an executable's location
Sometimest here's more than one version of an executable program installed on the system. To determine the exact location of a given command, use 
`which command`

## Getting a command's documentation

`help` for shell builtins

`help command` displays a page of documentation for that command

Notation: square brackets in the description of a command's syntax indicate optional items. A vertical bar | indicates mutually exclusive items.
`cd [-L|[-P][-e]]] [dir]`
means `cd` can be followed by either `-L` or `-P`, and if the `-P` option is specified, `-e` can also be used, and the `dir` argument is also optional

`--help` displays usage information, a description of the command's supported syntax and options

`man` displays a program's manual page

Man page organization by section
1: user commands
2: programming interfaces for kernel system calls
3: programming interfaces for the C library
4: special files such as device nodes and drivers
5: file formats
6: games and amusements
7: miscellaneous
8: system administration commands

You can refer to a specific section of the manual to find what you're looking for: `man section searchTerm`

You can also search for possible mnatches based on a search term: `apropos searchTerm` or `man -k searchTerm`

`whatis` displays one-line man page descriptions

## creating our own commands with alias

Put more than one command on a line by separating each with a semi-colon
`command1; command2; command3`

`alias name='string'`
`alias foo='cd /usr; ls; cd-'`

You can `type` your alias to see what it contains
`type foo` -> `foo is aliased to 'cd /usr; ls; cd -'`

To remove an alias, use `unalias`

To see all aliases defined within an environment, use `alias` with no args

Aliases vanish when your shell session ends.