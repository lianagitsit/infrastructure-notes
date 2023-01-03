# Package Management

A method of installing and maintaining software, which eliminates or reduces the need to download and compile source code to install software. 

## Packaging systems

Different distributions use different packaging systems. 

There are two main packaging technologies: Debian-style (.deb) and Red Hat-style (.rpm)

Distributions like Debian, Ubuntu, and Raspbian use the Debian-style system

A *package file* is the basic unit of software in a packaging system. It is a compressed collection of files that comprise the software package.

Programs are rarely "standalone" but rely on the presence of other software to function. *Shared libraries* provide essential services to more than one program. If a package requires a shraed resource such as a library, it is said to have a *dependency*. Package management systems provide some method of *dependency resolution* to ensure all shared resources are installed when the package is installed.

Package management systems usually consist of two types of tools:
* low-level tools that handle tasks such as installing and removing package files
* high-level tools that perform metadata searching and dependency resolution

Debian-style distributions 
low-level: `dpkg`
high-level: `apt-get`, `apt`, `aptitude`

`apt-get` is the tool for handling packages. May be considered the user's "back-end" to other tools using the APT library. 

For example, to install the emacs text editor from an apt repository, use
`apt-get update; apt-get install emacs`

Remove a package with `apt-get remove package_name`
`apt-get remove emacs`

## Updating packages from a repo

The most common package management task is keeping the systems up to date with the latest versions of packages.
`apt-get update; apt-get upgrade`
will apply all available updates to the installed packages

## determining whether a package is installed

`dpkg -s package_name`

