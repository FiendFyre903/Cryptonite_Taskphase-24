# Pondering Paths

## 1. The PATH variable

There is a special shell variable, called `PATH`, that stores a bunch of directory paths in which the shell will search for programs corresponding to commands.

Without `PATH`, commands (like `ls`, `cd`, etc ) wont work.

**Solution**
```
hacker@path~the-path-variable:~$ export PATH
hacker@path~the-path-variable:~$ PATH=""
hacker@path~the-path-variable:~$ /challenge/run
Trying to remove /flag...
/challenge/run: line 4: rm: No such file or directory
The flag is still there! I might as well give it to you!
pwn.college{cohe_e7muHvfrvye86cHXXN2LjT.dZzNwUDLxEzN0czW}
```

## 2. Setting PATH

We can add more paths to the `PATH` variable to allow us to run commands directly. In this level we simply overwrite the existing data, but normally we would add a new path to the `PATH` variable so it knows where to look.

**Solution**
```
hacker@path~setting-path:~$ export PATH
hacker@path~setting-path:~$ PATH=/challenge/more_commands/
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{MrdsHed6f8dCFfYeOqk77Qq_ucj.dVzNyUDLxEzN0czW}
```

## 3. Adding commands

First we create a file called `win` and using a text editor, we write `cat /flag` in it. Then we make `win` executable by all.

`PATH` already contains multiple essential directories, and overriding that will not allow any commands that depend on `PATH` to run without being invoked with their full path. In this case we still need `cat` to work. 

So, to save the previous data of `PATH`, instead of overriding, we can append the path to the `win` command we created.

**Solution:**
```
hacker@path~adding-commands:~$ nano win
hacker@path~adding-commands:~$ cat win
cat /flag
hacker@path~adding-commands:~$ chmod +x win
hacker@path~adding-commands:~$ echo $PATH
/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
hacker@path~adding-commands:~$ PATH="$PATH:/home/hacker"
hacker@path~adding-commands:~$ echo $PATH
/run/challenge/bin:/run/workspace/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/home/hacker
hacker@path~adding-commands:~$ /challenge/run
Invoking 'win'....
pwn.college{AGAFggSQpgDB6PvDcClqAFRzThL.dZzNyUDLxEzN0czW}
```

## 4. Hijacking Commands

The way PATH is scanned, is from left to right, so once a valid directory is found containing the command, it no longer searches. 

So if we make our own `rm` command and put its path before the path of the original `rm` command, our command will be the one thats executed.

```
hacker@path~hijacking-commands:~$ PATH=/home/hacker:$PATH
hacker@path~hijacking-commands:~$ nano rm
hacker@path~hijacking-commands:~$ cat rm
cat /flag
hacker@path~hijacking-commands:~$ /challenge/run
Trying to remove /flag...
Found 'rm' command at /home/hacker/rm. Executing!
pwn.college{MEJKYhVOxDSSB3ONrSjZDvUdTdw.ddzNyUDLxEzN0czW}
```