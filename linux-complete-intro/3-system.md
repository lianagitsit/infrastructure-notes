# Exploring the system

## list

Along with using `ls` to see the files in your current directory, you can also spercify the directory you want to see the files in with `ls /[dir]`

View multiple directories separated by spaces

Change the format to see more detail
`ls -l` (`-l` is the long format)

Example:
`-rw-r--r-- 2 root root 4096 Dec 13 13:28 fun`
ls long listing fields:
`-rw-r--r--` Access rights to the file. The first char indicates the type of file. A leading dash means a regular file, while a `d` means a directory. The next three chars are the access rights for the file's owner, the next three are for members of the file's group, and the final three are for everyone else.
`2` File's number of hard links.
`root` Username of the file's owner
`root` Name of the group that owns the file
`4096` Size of the file in bytes
`Dec 13 13:28` Date and time of the file's last modification
`fun` Name of the file

## Command format

`command -options arguments`

`ls -lt --reverse`
list the dir contents in long format sorted by modification time, in reverse

**command options are case sensitive**

## Determine file type

File extensions don't have the same meaning in linux, so you could have a file named something.jpg but it's not actually a JPEG. 

To see a file's type, use the `file` command.

this is important because **in linux everything is a file**

## View file contents

View file contents with `less`

`less` allows you to examine human-readable text files, and scroll backward and forward through them

If you attempt to view a non-text file and it scrambles the terminal, recover by entering `reset`

## Symbolic links

When you list out directory contents in long format, you may see a file that has two names, like `libc.so.6 -> libc.2.6.so`

This is a file type called a symbolic link (or soft link or symlink).

When you have a program that requires a shared resource that has frequent version changes, you don't want to have to update every reference to the resource every time the version changes. 

Instead you can say, whenever I am referring to this resource, use this one. In this way, you give the resource an alias, and then you only have to update the one place when version changes.