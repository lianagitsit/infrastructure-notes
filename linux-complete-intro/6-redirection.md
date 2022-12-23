# Redirection

I/O redirection lets us redirect the input and output of commands to and from files, as well as connect multiple comands together into command **pipelines**

Programs such as `ls` send their results to a standard output (stdout) file and their status messages to a standard error (stderr) file. These files are linked to the screen and not saved into a disk file.

Normally output goes to the screen and input comes from the keyboard, but with redirection we can change that.

## Redirecting standard output

To redirect standard output to a file instead of to the screen, use the `>` redirection operator followed by the name of the file
`ls -l /usr/bin > ls-output.txt`
Creates a long listing of the files in /usr/bin and sends that to a text file instead of printing it to the screen

IMPORTANT: Redirecting output with `>` always rewrites the destination file.

To append the redirected output to another file instead of overwriting it, use `>>`

## Redirecting standard error

Use the file descriptor to redirect standard error

The shell references standard input, output, and error as 0, 1, and 2 respectively

So if you want to redirect the standard error response from a command, you can place the file descriptor immediately before the redirection operator:

`ls -l /bin/usr 2> ls-error.txt`

To redirect standard output and standard error to one file, precede the redirection operator with `&`

To suppress an error from a command, redirect it to a "bit bucket," a file which accepts input and does nothing with it, `/dev/null`

## Redirecting standard input

To display the contents of a file, use the `cat` command which reads one or more files and redirects them to standard output

`cat filename`

In the absence of filename args, `cat` copies standard input to standard output so you see the line of text repreated. if you just type `cat` then type some text and then `ctrl+D` to tell it you've reached EOF, you can then do `cat > lazy_dog.txt` and it will create that file with the text you entered in the last command.

## Pipelines

Pipelines read data from standard input and send it to standard output.

pipe output from command 1 into the input of command 2:
`command1 | command2`

`less` is often used with piping to display a paginated view of the output of any command.

Helpful for paginating and scrolling through output much better than standard output

`ls -l /usr/bin | less`

Put several commands together with pipe into a pipeline and you've created a filter.

Filters take input, change it somehow, and then output it.

Make a combined list of all programs in /usr/bin and /bin, sort them and view the output:
`ls /bin /usr/bin | sort | less`

Difference between `>` and `|` is that `>` redirects the output of the first command to another file, and `|` uses the first command's output as the input of the second command.

If you try to redirect output when you mean to pipe it, you could end up doing something really bad:
`ls > less` 
will overwrite `less`, destroying it altogether.
DON'T DO THAT!

### Report or omit repeated lines

`uniq` accepts a sorted list of data and removes any duplicates from the list

You can instead see the duplicates with the `-d` flag
`ls /bin /usr/bin | sort | uniq -d | less`

### Print word, line, and byte count

The `wc` (word count) command is used to display the number of words, lines, and bytes in files

It can be useful for printing out the number of items in a list:
`ls /bin /usr/bin | sort | uniq | wc -l`

### Print lines matching a pattern

`grep` is used to find text patterns within files.

`grep pattern filename`

When `grep` encounters that pattern in the file, it prints out the lines containing it

`-i` causes `grep` to ignore case when performing the search (searches are normally case-sensitive)

`-v` tells `grep` to print only those lines that do not match the pattern

### Print first / last part of files

`head` command prints the first 10 lines of a file, and `tail` prints the last 10. By default, both print 10 lines of text but this can be adjusted with `-n`

`head -n 5 ls-output.txt`
`ls /usr/bin | tail -n 5`

`tail` has an option that allows you to read files in real time, which is useful for watching the progress of logs as they are being written

Using `-f` `tail` continues to monitor the file and when new lines are appendeed they immediately appear on the display

### Read from stdin and output to stdout and files

`tee` read standard input and copies it to both std output (allowing the data to continue down the pipeline) and to one or more files

Here we capture the entire directory listing to `ls.txt` before `grep` filters the contents:
`ls /usr/bin | tee ls.txt | grep zip`

