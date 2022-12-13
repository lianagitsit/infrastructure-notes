# Manipulating Files and Directories

Common commands
cp: copy files
mv: move or rename files/dirs
mkdir create directories
rm remove files and dirs
ln create hard and sym links

## wildcards
Rapidly specify groups of filenames
also known as globbing
select filenames based on patterns of chars

* matches any char
? matches any single char
[chars] matches any char that is a member of the set [chars]
[!chars] matches any char that is not a member of the set
[[:class:]] matches any char that is not a member of the specified class

commonly used char classes:
[:alnum:] any alphanumeric char
[:alpha:] any alpha char
[:digit:] any numeral
[:lower:] any lowercase letter
[:upper:] any uppercase letter

wildcard examples:
* all files
g* any file beginning with g
b*.txt afile beginning with b followed by any chars and ending with /txt
Data??? any file beginning with Data followed by exactly three chars
[abc]* any file beginning with either an a, b, or c
BACKUP.[0-9][0-9][0-9] any file beginning with BACKUP. followed by exactly three numerals

Wildcards can be used in any command that accepts filenames as arguments

# copy files

`cp item1 item2` copies single file or dir into the other file or dir
`cp item... dir` copies multiple items (files or dirs) into a directory

The `-i` (or `--interactive`) flag means that before overwriting an existing file, prompt the user for confirmation. If this flag is not included, `cp` will silently (without warning) overwrite files.

`-r` or `--recursive` recursively copies directories and their contents. this option is required when copying directories

`-u` or `--update` when copying files from one dir to another, only copy files that either don't exist or are newer than the existing corresponding files in the destination direcotry. useful when copying large numbers of files as it skips files that don't need to be copied.

# move and rename files

`mv` performs moving and renaming files depending on how it is used. in both cases the original filename no longer exists after the operation.

`mv item1 item2` moves or renames the file or dir item1 into item2
`mv item... directory` moves one or more items from one dir to another

shares many of the same options as `cp` such as `-i` and `-u` and `-v` (verbose, displays informative messages as the move is performed)

## remove files and directories

`rm item...` deletes one or more files or dirs

rm options:
`-i` prompts user before deleting, will silently delete if not specified
`-r` rescursively deletes directories. if a directory being deleted has subdirectories, delete them too. this option must be specified to delete a directory.
`-f` or `--force` ignores nonexistent files and does not prompt. overrides the `--interactive` option.
`-v` display informative messages as the deletion is performed

Once you delete something with `rm` it's gone, there is no undelete option. Be careful with wildcards.

Using wildcards with rm:
test the wildcard first with `ls` so you can see the files that will be deleted, then press up arrow to recall the command and replace `ls` with `rm`

rm examples:
`rm file1` delete file1 silently
`rm -i file1` same as previous, but prompt the user for confirmation before the deletion is performed
`rm -r file1 dir1` delete file1 and dir1 and its contents
`rm -rf file1 dir1` same as previous, except that if either file1 or dir1 does not exist, rm will continue silently

## create links

`ln` is used to create either a hard link or a symlink in one of two ways

`ln file link` creates a hard link
`ln -s item link` creates a symbolic link where item is either a file or a dir

## hard links
By default, every file has a single hard link that gives the file its name. 

When you create a hard link you create an additional directory entry for the file.

Limitations of hard links:
1. A hard link cannot reference a file outside its ownf ile system. A link cannot reference a file that is not on the same disk partition as the link itself.
2. A hard link cnanot reference a directory.

Modern practice prefers symbolic links.

## symbolic links
Created to overcome the limitations of hard links.

Symlinks work by creating a special type of file that contains a text pointer to the referenced file or directory.

A file pointed to by a symlink and the symlink itself are largely indistinguishable from each other. If you write something to the symbolic link, the reference file is written to. But when you delete a symlink, only the link is deleted, not the file. If you delete the file before the link, the link remains, but points to nothing, and then it is said to be a broken link.

# playground

Shorthand for the current working directory is `.` 
Copy `/etc/passwd` into current working directory:
`cp /etc/passwd .`

Files are made up of two parts:
1. The data part containing the file's contents
2. The name part that holds the file's name

When we create hard links, we are actually creating additional name parts that refer to the data parts
