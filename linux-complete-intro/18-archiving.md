# Archiving and backup

File compression programs:
`gzip` compress or expand files
`bzip2` a block sorting file compressor

Archiving programs:
`tar` tape archiving utility
`zip` package and compress files

`rsync` Remote file and directory sync

## compressing files

Data compression is the process of removing redundancy from data

`gzip` compresses one or more files. When executed it replaces the original file with a compressed version of the original.

The corresponding `gunzip` is used to restore compressed files to their original form

## archiving

Archiving is the process of bundling many files together into one large file

## sync

Keep a remote dir and a local dir in sync with `rsync`
works by detecting the differences between them and doing the minimum amount of work needed to align them

