# Reading Keyboard Input

`read` builtin is used to read a single line of standard input. It can read keyboard input or be redirected to read a line of a file.

`read [-options] [variable...]`

where options are one or more of the available options and variable is the name of one or more variables used to hold the input. 

If no variable is specified, the default `REPLY` variable contains the line of data

`read` assigns fields from standard input to the specified variables.

```
echo -n "Please enter an integer -> "
read int

if [[ "$int" ...]]
```

Here, `echo` with `-n` suppress the trailing newline so the user can enter their input on the same line as the prompt.

Then `read int` assigns the input to the variable `int`, and we use that variable in our conditional.

`read` can assign input to one or more variables:
`echo -n "Enter one or more integers > "`
`read var1 var2 var3`

If the input contains more integers than `read` has variables to assign, the last variable will contain all of the overflow integers.

If the input contains fewer ints than `read` has variables, the remaining variables will be assigned empty strings.

If no variables are listed after `read`, the shell variable `REPLY` holds the input.

`read` options: 
`-a [array]` Assign the input to `array`
`-d [delimiter]` The first char in the string `delimiter` is used to indicate the end of the input rathe than a newline char
`-e` Use readline to handle input. This permits input editing in teh same manner as the command line.
`-i [string]` Use `string` as a default reply is the user simply presses enter (requires `-e`)
`-n [num]` Read `num` chars of input rather than an entire line
`-p [prompt]` Display a prompt for input using the string `prompt`
`-r` Raw mode, do not interpret backslash as escapes

