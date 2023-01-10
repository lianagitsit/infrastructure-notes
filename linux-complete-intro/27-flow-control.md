# Flow Control: Branching With If

When we use expansion to run commands within a script, we might encounter some commands that require superuser privileges, and thus won't work unless we have some way of adapting our script to the privileges of the user running it.

```
if commands; then
    commands
elif commands; then
    commands
else
    commands
fi
```

## exit status

Commands issue a vlaue to the system when they terminate, called exit status, which is an integer in the range of o to 255 and indicates the success or failure of its execution.

A value of 0 indicates success and anything else is a failure.

The parameter `$?` shows the exit status following the execution of a command:
`ls /usr/bin` command
`echo $?` print exit status of last command

## test

The `test` command is the most common command used with `if`

`test` is used to evaluate whether an expression is true or false. Returns 0 if true and 1 if false.

It can be written in two ways:
`test command`
`[ command ]` this syntax is more common

Use `test` to evaluate the status of files, such as:
`-e file` file exists
`-r|-w|-x file` file is readable, writable, or executable for the effective user

```
#!/bin/bash

FILE=~/.bashrc

if [-e "$FILE"]; then
    echo "$FILE is a regular file."
    fi
    if [-d "$FILE"]; then
        echo "$FILE is a directory."
    fi
    if [-r "$FILE"]; then
        echo "$FILE is readable."
    fi
else
    echo "$FILE does not exist."
    exit 1
fi

exit
```

Note that the parameter $FILE is quoted within the `if` expressions. This is not required to syntactically complete the expression. It is a defense against the parameter being empty or only containing whitespace. 

If the parameter expansion of $FILE were to be empty, it would cause an error. The operators would be interpreted as non-null strings rather than operators.

If we were to convert this script to a shell function to use as part of a larger program, we could replace the `exit`s with `return` statements

## string expressions

`test` can be used to evaluate strings, true if:
`string` string is not null
`-n string` length is > 0
`-z string` length == 0
`string1 = string2, string1 == string2` strings are equal. can use either `=` or `==` but `==` is preferred
`string1 != string2` not equal

## integer expressions

true if:
`int1 -eq int2` equal
`int1 -ne int2` not equal
`int1 -le int2` less than or equal
`int1 -lt int2` less than
`-ge` greater than or equal
`-gt` greater than

## a more modern version of test

Modern versions of bash include a compound command that acts as an exhanced replacement for test
`[[ expression ]]`
where `expression` evaluates to either a true or false result. `[[ ]]` is similar to `test` and supports all of its expressions but adds a new string expression:
`string =~ regex`

`string =~ regex` returns true if string is matched by the extended regex

`[[ "$INT" =~ ^-?[0-9]+$ ]]` evaluates to true if the integer begins with an optional minus sign, followed by a number between 0 and 9 one or more times.

`[[ ]]` also adds support for using `==` to match patterns the same way pathname expansion does, as in `[[ $FILE == foo.* ]]`

## (( )) for integers

 `(( ))` performs arithmetic truth tests

`(( INT == 0))`
`(( INT < 0 ))`
`(( ((INT % 2 )) == 0 ))`

## combining expressions

There are three logical operators for `test`
`-a` AND
`-o` OR
`!` NOT

And for `[[ ]]` and `(( ))`
`&&` AND
`||` OR
`!` NOT

`!` reverses the outcome of an expression

## control operators: another way to branch

`bash` provides two control operators that can perform branching: `&&` and `||`

`command1 && command2`
command2 is executed if and only if command1 is successful

`command1 || command2`
command2 is executed if and only if command1 was unsuccessful

`mkdir temp && cd temp`
Create a directory "temp" and, if successful, change the current dir to temp

`[[ -d temp ]] || mkdir temp`
test for the existence of a directory "temp" and if unsuccessful, make one