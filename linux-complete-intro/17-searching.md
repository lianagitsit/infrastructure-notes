# Searching For Files

`locate` find files by name
`find` search for files in a dir hierarchy
`xargs` build and execute command lines from standard input

## find

predefined `find` actions:
`-delete` to delete the currently matching file
`-ls` perform the equivalent of `ls -dils` on the matching file, sending output to stdout
`-print` output the full pathname of the matching file to standard output 
`-quit` quits once a match has been made

find a file in a dir:
`find [dir] -name [filename]`