# Starting a Project

## here documents

A "here document" or "here script" is a form of I/O redirection in which we embed a body of text into our script and feed it into the standard input of a command.

`command << token`
`text`
`token`

where `command` if the name of command that accepts standard input and token is a string used to indicate teh end of teh embedded text.

We modify our script to remove `echo` before the html string and remove the quotes from the html and add 
`cat << _EOF_`
[html]
`_EOF_`

Instead of `echo` we now use `cat` and a here document. The string `_EOF_` (end of file) is the token and marks the end of the embedded text.

The advantange ofa here document is that by default single and double quores within here documents lose their special meaning to the shell and are treated as ordinary characters.

