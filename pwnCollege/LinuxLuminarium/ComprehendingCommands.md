# Comprehending Commands

## 1. cat: not the pet, but the command

*I typed `ls` first to get the list of files in the home directory.Then I used `cat` to read the file named **flag***

**Note:-**
1. **ls** </br>
   The ls command is used to list the contents of a directory, in this case the home directory.</br>
   `ls`

2. **cat**<br>
   The cat command prints the data present in files of two types - text files and certain compatible binary files.<br>
   `cat filename`

**Solution:** </br>

`ls`<br>
`cat flag`<br>

## 2. Catting absolute paths

*A simple change of using the full path gives the flag*

**Solution:**

``cat /flag``

## 3. More catting practice

*Using `find / -iname flag*` gave me a long list of files named flag across the directories, but did not help narrow down the correct location. `find / -name "flag"` gave a shorter list of paths of which 5 were accesible. So i used cat on all of them, the second path gives the flag.*<br>

*Second option is to automatically **cat** the results of **find** using `-exec` with the argument **cat***

**Note:-**<br>
1. **find** <br>
   The find command is used to find files that fulfil specified conditions.<br>
   `find`<br>

    *`-exec` option is used to execute a command on each file found.<br>
    `cat` is the command to output the contents of a file.<br>
    `{}` is a placeholder for the file name found by `find`.<br>
    `\;` is used to indicate the end of the `-exec` command. It tells find to execute the command once per file found.*

**Solution:**

`find / -name "flag"`<br>
`cat /usr/share/lintian/flag`

OR

`find / -name "flag" -exec cat {} \;`

## 4. Grepping for a needle in a haystack

*Using `grep` on the file with the search-string **pwn.college** gives us one match, which is the flag.*

**Note:-**<br>
1. **grep** </br>
The grep command is used to find patterns in a given file.<br>
`grep 'pattern' filename`

**Solution:**

`grep pwn.college /challenge/data.txt`

## 5. Listing files

*Using `ls` to get the contents of the challenge directory*

**Solution:**

`cd /challenge` <br>


