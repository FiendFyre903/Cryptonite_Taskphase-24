# Pondering Paths

## 1. The Root

*Executing the **pwn** program using the absolute file path from the root gives the flag*

**Command used:**

`/pwn`

## 2. Program and absolute paths

*Executing the **run** program located in the **challenge** directory which itself is located in the home directory gives the flag. To be noted that `cd challenge` did not work*

**Command used:**

`/challenge/run`

## 3. Position thy self

*Navigating to **/** using cd and then executing the run program.*

*NOTE - <br>
`challenge/run` does not work.<br>
`cd/challenge` does work, navigating to /challenge, however /run does not work as it does not meet the requirements of the problem.<br>
Necessary to to use the full path*

**Solution:**

`cd /`<br>
`/challenge/run`

## 4. Position Elsewhere

*`/challenge/run` gives a message suggesting to cd to **/proc/67/fd**.       Executing `/challenge/run` from said directory gives the flag.*

**Solution:**

`cd /proc/67/fd`<br>
`/challenge/run`


## 5. Position Yet Elsewhere

*`/challenge/run` gives a message suggesting to cd to **/usr/share/doc/fontconfig**. Executing `/challenge/run` from said directory gives the flag.*

**Solution:**

`cd /usr/share/doc/fontconfig`<br>
`/challenge/run`

## 6. Implicit relative paths, from /

*Navigating to **/** and executing run from cwd gives the flag.*

*Note- <br>
`.` refers to current working directory(cwd). <br>
`..` refers to parent of cwd.*

**Solution:**

`cd /`<br>
`challenge/run`

## 7. Explicit relative paths, from /

*`challenge/run` from **/** lets us know that we need to start with `./` which really is redundant and does not change the effect of the command, so `./challenge/run` works the same, giving the flag.*

**Solution:**

`cd /`<br>
`./challenge/run` **OR** `./././challenge/run`

## 8. Implicit relative path

*simply navigating to **/challenge** and then executing **run** while explicity mentioning the current directory using`.` successfully gives the flag.*

**Solution:**

`cd /challenge`<br>
`./run`

## 9. Home sweet home

*Meeting the requirements by using a 1-character long file name, and using `~` to represent the home directory, resulting in `~/a`, meaning a is in the home directory. Using this parameter gives the flag.*


*NOTE- <br>
`/challenge/run` is the command, `~/a` is the argument.*

**Solution:**

`/challenge/run ~/a`

