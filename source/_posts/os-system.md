---
title: Difference between subprocess.Popen and os.system
date: 2012-05-09 10:50:27
tags:
---
os.system is equivalent to Unix system command, while subprocess was a helper module created to provide many of the facilities provided by the Popen commands with an easier and controllable interface. Those were designed similar to the Unix Popen command.

system() executes a command specified in command by calling /bin/sh -c command, and returns after the command has been completed

where as

The popen() function opens a process by creating a pipe, forking, and invoking the shell.

If you are thinking, which one to use, then use subprocess definitely because you have all facilities for execution, plus additional control over the process.

Link: http://stackoverflow.com/questions/4813238/difference-between-subprocess-popen-and-os-system