# Seeing the World As the Shell Sees It

`echo` displays a line of text

## Expansion

Each time we type a command and press enter, bash performs several substitutions upon the text before it carries out our command.

The process that makes this happen is called expansion. We enter something, and it is expanded into something else before the shell acts upon it.

`echo` is a shell builtin that performs a simple task, which is just printing its text arguments on standard output

Any argument passed to `echo` gets displayed.

But if you type 
`echo *`
You will not see `*` in output, you will see
`Desktop Documents Music Pictures`

The `*` char is a wildcard which means match any character in a file name, and the shell expands it into something else before `echo` is executed.

When the enter key is pressed, the shell automatically expands any qualifying characters on the command line before the command is carried out, so the echo command never saw the *, only its expanded result.

display hidden files with `ls -A` (`-A` = almost all)

## Arithmetic expansion

You can use the terminal as a calculator
`echo $((2 + 2))`

Arithmetic expansion supports only whole numbers

## Brace expansion

Create multiple text strings from a pattern containing braces

`echo Front-{A,B,C}-Back`
> Front-A-Back Front-B-Back Front-C-Back

The most common application of this technique is to make lists of files or directories to be created, for example if you needed to make a large number of directories to organize files by date.

## Parameter expansion

More useful in shell scripts than in the terminal

Basically variables

## Command substitution

Allows the output of a command to be used as an expansion

Pass the result of a command as an argument to another command

`echo $(ls)`
uses the output of `ls` as the argument for `echo` and prints the output of `ls`

Entire pipelines can be used as substituted commands

## Quoting

Selectively suppress unwanted expansions, basically escaping expansions

If you place text inside double quotes, all special characters used by the shell lose their special meaning and area treated as ordinary characters. The exceptions are `$` and `\` and the backtick.

Parameter expansion, arithmetic expansion and command substitution still take place within double quotes.

Unquoted spaces, tabs, and newlines are not considered to be part of the text, they serve only as separators.

Single quotes are used when we need to suppress *all* expansions.

## Escaping characters

When you want to quote only a single character, precede it with a backslash, called an escape character in this context. Often this is done inside double quotes to selectively prevent expansion.

To include a special character in a filename, do
`mv bad\&filename good_filename`

To allow a backslash character to appear, escape it by typing `\\`

Expansions and quoting are the most important subjects to learn about in the shell

