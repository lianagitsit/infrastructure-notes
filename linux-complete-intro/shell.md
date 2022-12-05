# The Linux Command Line: A Complete Introduction

"Freedom is the power to decide what your computer does, and the only way to have this freedom is to know what your computer is doing. Freedom is a computer that is without secrets, one where everything can be known if you care enough to find out."

What a banger.

## What is the shell?

When we speak of the command line, we're really referring to the **shell**. The shell is a program that takes keyboard commands and passes them to the operating system to carry out. 

If the last character of the **shell prompt** is a #, rather than a $, then the terminal session has superuser privileges.

The **command history** of most Linux dists contains the last 1,000 commands by default.

## How I Set Up My Shell

Built a docker image using Dockerfile.linuxplayground
- Pulled the latest Ubuntu image, which comes minimized and therefore doesn't have commands like `man` and `cal`
- unminimize still didn't see those commands working, so used a Dockerfile to install the files in the container and then unminimize them

`docker build -f Dockerfile.linuxplayground . -t ubuntu:unminimized`

Builds and names my Ubuntu image

`docker run -it ubuntu:unminimized`

Runs my Ubuntu container