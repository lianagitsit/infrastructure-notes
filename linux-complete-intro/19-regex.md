# Regular Expressions

Symbolic notations used to identify patterns in text

## grep

The main program we'll use with regex is `grep`, which stands for "global regular expression print." Neat!

`grep` searches text files for text matching a specified regex and outputs any line that matches to stdout

`grep [options] regex [file...]`

commonly used `grep` options:
`-i` ignore case
`-v` invert, show lines without matches
`-c` count, print number of matches instead of the lines
`-l` file with matches, print name of files that contain matches instead of the lines
-`L` files without matches
`-n` line number, prefix each match with line number
`-h` suppress the prefix of filenames on each match


## metacharacters and literals

In addition to literals, regex may also include metacharacters that are used to specify more complex matches

These metacharacters are:
`^ & . [ ] { } - ? * + ( ) | \`

All other characters are considered literals

**NOTE** that many of the regex chars are also chars that have meaning in shell expansion. When we pass regex containing metachars on the command line, they must be enclosed in quotes to prevent the shell from attempting to expand them.


## The Any Character

To match any character, use `.`

Included in a regex, the dot will match any character in that character position.

`grep -h '.zip' dirlist*.txt`
Searched for any line in our dirlist files that contains the regex `.zip`.
- Note that this does not return the program `zip`, because when we add `.` we increase the required length of the match from 3 chars to 4.

## Anchors

`^` and `$` are treated as anchors in regex.

Anchors cause the match to occur only if the match is found at the beginning of the line (`^`) or at the end of the line (`$`).

Find a five-letter word whose third letter is j and the last letter is r
`grep '^..j.r$' /usr/share/dict/words`

## bracket expressions and character classes

Bracket expressions match a single character from a specified set of characters. So of the characters between brackets, any single character that matches one of them will satisfy the expression.

`grep '[bg]zip' dirlist*.txt`
matches any line that contains `bzip` or `gzip`

Metacharacters lose their special meaning inside brackets, but there are two conditions in which two metas inside brackets have different meanings than their literals. `^` for negation and `-` for character ranges.

### negation

If the first characte inside brackets is a `^` caret, the match must NOT contain the following characters at the given position in the string.

If our match is `[^bg]zip` then we will not get `bzip` or `gzip` OR `zip`, because the brackets indicate that a character is required in that position, just not the ones specified.

The caret invokes negation only if it is the first char in the bracket set, otherwise it's just a literal character.

### traditional char ranges

A dash `-` can be used to represent any range of characters that can be expressed as a range: `[A-Z]`

Multiple ranges can be combined into one bracket set:
`[A-Za-z0-9]`

To include a dash character literal in the char set, make it the first char in the set: `[-A]` will match "-A"

## alternation
Use the `-E` flag with `grep` to signify the use of extended regex, or use `egrep`

Alternation allows a match to occur from among a set of expressions.

`AAA|BBB` matches "AAA" or "BBB"
`^(bz|gz|zip)` matches any string that starts with bz, g, or zip.
`^bz|gz|zip` matches any string that starts with bz, and any string that contains gz or zip anywhere.

## quantifiers

extended regex support several ways to specify the number of times an element is matched.

`?` matches an element zero or one time
This basically means to make the preceding element optional

`*` matches an element zero or more times
This also means the element is optional, but it can appear any number of times, not just once

`+` matches an element one or more times
The element requires at least one element of the preceding character to match

`{}` match an element a specific number of times
`{n}` match the preceding element only if it appears n times
`{n,m}` match only if it occurs at least n but no more than m times
`{n,}` match if it occurs n or more times
`{,m}` match if it occurs no more than m times


