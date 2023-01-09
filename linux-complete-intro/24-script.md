# Writing Your First Script

## How to write a shell script

1. Write a script.
2. Make the script executable: set the script's permissions to be executable.
3. Put the script somewhere the shell can find it: place the scripts in one of the directories the shell automatically searches for exec files when no explicit path is specified.

## script file format

`#! /bin/bash`
`#!` is a shebang, used to tell the kernel the name of the interpreter that should be used to execute the script that follows. Every shell script should include this as its first line.

## script file location

For the script to run, we must precide the script name with an explicit path, or we get an error.
`./hello_world` vs `hello_world`

The system searches a list of directories each time it needs to find an executable program, if no explicit path is defined. This list is stored in the PATH variable.

If our script were located in any of the locations in PATH, we would be able to run `hello_world` without specifying a path, just like any other executable.

Make a directory called `bin`, move `hello_world` into it, and then add `bin` to `PATH` by adding
`export PATH=~/bin:"$PATH"`
to `.bashrc` file

Apply the change to the current terminal session by "sourcing" (or having the shell reread) the bash file.
`source ~/.bashrc` or `. ~/.bashrc`


## good locations for scripts

`~/bin` is a good place to put scripts intended for personal use.

`/usr/local/bin` is traditionally used for scripts that everyone on a system is allowed to use

`/usr/local/sbin` for use by the system administrator

