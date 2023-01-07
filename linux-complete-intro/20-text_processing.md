# Text Processing

Programs that are used to "slice and dice" text

`cat` concatenate files and print on standard output
`sort` sort lines of text files
`uniq` report or omit repeated lines
`cut` removes sections from each line of files
`paste` merge lines of files
`join` join lines of two files on a common field
`comm` compare two sorted files line by line
`diff` compare files line by line
`patch` apply a diff file to an original
`tr` translate or delete characters
`sed` stream editor for filtering and transforming text
`aspell` interactive spell checker

## cat

The `-A` option prints non-printing characters so you can see whitespace or control characters that might appear in a string.

`cat` also has options for modifying text:
`-n` numbers lines
`-s` suppresses the outoput of multiple blank lines

## sed

short for 'stream editor', sed performs editing on a stream of text, either a set of specified files or standard input

in general, it works by being given either a single editing command on the command line or the name of a script file containing multiple commands, and it then performs those commands on each line in the stream of text

`echo "front" | sed 's/front/back'`
Produce a one word stream of text with `echo` and pipe it into `sed` which then carries out the instruction in `s/front/back`, which is basically find and replace, and output is `back`

Commands in sed begin with a single letter. In this example the `s` command is subsitution. The following slash is a delimiter and can be any character: `s_front_back` would also work.

Most sed commands are preceded by an address, which specifies which lines will be edited. Without the address, every line will be edited. The simplest address is the line number: `1s/front/back`

