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



**Solution**
```
hacker@path~setting-path:~$ export PATH
hacker@path~setting-path:~$ PATH=/challenge/more_commands/
hacker@path~setting-path:~$ /challenge/run
Invoking 'win'....
Congratulations! You properly set the flag and 'win' has launched!
pwn.college{MrdsHed6f8dCFfYeOqk77Qq_ucj.dVzNyUDLxEzN0czW}
```