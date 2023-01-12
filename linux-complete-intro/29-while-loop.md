# Flow Control: Looping with While / Until

`while commands; do commands; done`

## breaking out of a loop

`break` immediately terminates a loop and program control resumes with the next statement following the loop

`continue` causes the remainder of the loop to be skipped and program control resumes with the next iteration of the loop

## until

continues until it received a zero exit status

`until [[ "$count" -gt 5 ]]; do`

## reading files with loops

`while` and `until` can process standard input, which allows files to be processed using loops.

To redirect a file to a loop, place the redirection operator after the `done` statement: `done < distros.txt` 

The loop will use `read` to input the fields from the redirected file. `read` will exit after each line is read wirtha zero exist status until EOF is reaached.