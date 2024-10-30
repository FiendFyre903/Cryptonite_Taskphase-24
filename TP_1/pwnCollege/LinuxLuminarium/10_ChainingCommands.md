# Chaining Commands

## 1. Chaining with semicolons

`;` can be used to chain commands so instead of entering them one by one, we can enter them all at once to run one after another

Ex: `command_1; command_2; command_3`

**Solution:**
```
hacker@chaining~chaining-with-semicolons:~$ /challenge/pwn;/challenge/college
Yes! You chained /challenge/pwn and /challenge/college! Here is your flag:
pwn.college{oj52SCHAlWiKwRCyPjbVLGwUv1j.dVTN4QDLxEzN0czW}
```

## 2. Your first shell script

We can use shell scripts to run a series of commands, similar to a `.py` python file. here we use the extension `.sh`(It is only for visual.). Since linux doesnt decide file type based on extension, this is not a requirement, just standard practice.

To write a shell script, we use a text editor such as `vim`. 

The basic commands of `vim`:

Create file - `vim filename`

Modes in the vim editor -
1. clicking `i`/`a` enables insert mode.
2. `:` allows us to write commands inside vim (commands we want to run to interact with vim.) <br>
    `:q` - Quit the editor <br>
    `:q!` - Quit without saving changes i.e. discard changes. <br>
    `:wq` - Save the changes and quit the editor

    Link for other vim commands and help - <br>
    https://www.geeksforgeeks.org/basic-vim-commands/

Finally to execute the shell script we use `bash`

`bash file` 

**Solution:**
```
hacker@chaining~your-first-shell-script:~$ vim x.sh
hacker@chaining~your-first-shell-script:~$ bash x.sh
Great job, you've written your first shell script! Here is the flag:
pwn.college{AucxGWuc4E0q11-YE1DaQwcfgYM.dFzN4QDLxEzN0czW}
```

## 3. Redirecting script output

`bash` is just like any other command, its outputs can be piped and redirected in all the same ways.

So, if we put multiple commands in one file and bash it, the outputs come out as one output and it can be piped into another command, essentially making it so that we are piping the outputs of multiple commands into one instance of another command.

**Solution:**
```
hacker@chaining~redirecting-script-output:~$ vim x.sh
hacker@chaining~redirecting-script-output:~$ cat x.sh
/challenge/pwn
/challenge/college
hacker@chaining~redirecting-script-output:~$ bash x.sh | /challenge/solve
Correct! Here is your flag:
pwn.college{EmZ6TxhcHECVr3oV-AiefCqM0cE.dhTM5QDLxEzN0czW}
```

## 4. Executable shell scripts

invoking `bash` every single time is unnecessary. we can simply make the file -executable by using `chmod +x script.sh`. After that we can simply execute the file like any other and it will work like bash.

**Solution:**
```
hacker@chaining~executable-shell-scripts:~$ vim script.sh
hacker@chaining~executable-shell-scripts:~$ chmod +x script.sh
hacker@chaining~executable-shell-scripts:~$ ./script.sh
Congratulations on your shell script execution! Your flag:
pwn.college{Ij2vOfseD8PwTWZYGabVMRSMyy2.dRzNyUDLxEzN0czW}
hacker@chaining~executable-shell-scripts:~$ cat script.sh
/challenge/solve
```