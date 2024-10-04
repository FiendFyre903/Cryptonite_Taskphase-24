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

*Using `ls` to get the contents of the challenge directory, which gave us a file named **17022-renamed-run-24227** which when executed, gives the key.*

**Solution:**

`cd /challenge` <br>
`./17022-renamed-run-24227`

## 6. Touching files

*The level asks to create to files in the `/tmp` directory. This can be achieved using the `touch` command with the filename as the argument.Finally, executing the run command in the challenge directory gives the flag.*

**Note:-**
1. **touch** </br>
   The touch command is used to lcreate a blank new file in the current directory. It takes the filename(s) as an argument</br>
   `touch file_name`

**Solution:**

`cd /tmp`<br>
`touch pwn`<br>
`touch college`<br>
`/challenge/run`

## 7. Removing files

*This level requires us to delete a file named remove_me located in the home dierctory using the `rm` command. Removing the file and then executing the given **check** file gives the flag.*

1. **rm** </br>
   The touch command is used to delete an exisiting file in the current directory. It takes the filename as an argument</br>
   `rm file_name`

**Solution:**

`rm delete_me`<br>
`/challenge/check`

## 8. Hidden files

*This level highlights an option(flag) of the `ls` command. The flag `-a` shows all hidden files along with regualar files. Hidden files are files with their name starting with a  `.`, for example `.hidden`.*<br>
*The first step in this level is to `cd` to the `/` directory. Using the command `ls -a` gives one hidden file with the word **flag** in its name. 
Using the `cat` command to read this file gives the flag.*

**Solution:**

`cd /`<br>
`cat .flag-253232925318680`

## 9. An epic Filesystem quest

*This level was a series of clues leading to the flag, The conditions/rules for the next clue were of 3 types :-* <br>

1. Hidden files - The way to overcome this was using `ls -a path`, path representing the **full_path**/**relative_path** of the directory whose contents we want to see.

2. Not allowed to `cd` into folder - The way to do this was very similar, simply use `l -a path` and then the `cat` command with the **full_path**/**relative_path** as argument.

3. Forced to `cd` into the next clue's directory - This could be directly achieved by `cd full_path`

<br>

**Solution:**

`ls -a`<br>
`cat SNIPPET`<br>
`cd /usr/lib/python3/dist-packages/sphinx/directives`<br>
`ls -a`<br>
`cat .INFO`<br>
`ls -a /usr/local/lib/python3.8/dist-packages/jedi/third_party/django-stubs/django-stubs/contrib/staticfiles/management`<br>
`cat /usr/local/lib/python3.8/dist-packages/jedi/third_party/django-stubs/django-stubs/contrib/staticfiles/management/TEASER-TRAPPED`<br>
`cd /usr/lib/python3/dist-packages/importlib_metadata-1.5.0.egg-info`<br>
`ls -a`<br>
`cat WHISPER`<br>
`ls -a /opt/busybox/busybox-1.33.2/include/config/feature/inetd/support`<br>
`cat /opt/busybox/busybox-1.33.2/include/config/feature/inetd/support/TIP-TRAPPED`<br>
`ls -a /usr/share/perl/5.30.0/Archive/Tar`<br>
`cat /usr/share/perl/5.30.0/Archive/Tar/.MEMO`<br>
`cd /usr/share/doc/xml-core`<br>
`ls -a`<br>
`cat HINT`<br>
`ls -a /usr/lib/python3/dist-packages/jedi/third_party/typeshed/third_party/2/scribe`<br>
`cat /usr/lib/python3/dist-packages/jedi/third_party/typeshed/third_party/2/scribe/REVELATION-TRAPPED`<br>
`cd /opt/aflplusplus/nyx_mode/QEMU-Nyx/ui/shader`<br>
`ls -a`<br>
`cat CLUE`

## 10. Making Directories

*This level requires the use of the `mkdir` command to make a new directory, as well as `touch` command to create a file in the new directory. After meeting the requirements, executing the **run** file gives the flag.*

**Note:-**
1. **mkdir** </br>
   The `mkdir` command is used to create a new directory. It accepts a full path with new directory name or just the name of the new directory. If just a name without path is given, it defaults to creating the directory in the current directory.</br>
   `mkdir path/name`

**Solution:**

`mkdir /tmp/pwn`<br>
`touch /tmp/pwn/college`<br>
`/challenge/run`

## 11. Finding files

*This level requires us to use the `find` command along with two options. `-name`, which searches for files/directories matching whatever name is given, and `-type` which specifes the type of the file/directory to be found. We also specify `/` as the path from where to start the search.*<br>
*Using find, we get one file that we can access, along with many that we dont have permission for. Using cat on the file found gives us the flag*


**Solution:**

`find / -name flag -type f`<br>
`cat /usr/lib/python3/dist-packages/matplotlib/testing/__pycache__/flag`


## 12. Linking files

*Symbolic link is a method to make one file point to another file, so any operation performed to it will effectively be performed on the file it points to. This linking can be achieved using the `ln` command.*<br>
*In this level, we must link **not-the-flag** file to the **/flag** file.*

**Note:-**
1. **ln** </br>
   The `ln` command is used to create a symbolic link between two files, where one files acts like a pointer to the other file. `-s` option specifes that the type of linking is soft-linking. It is also possible to hard-link files.</br>
   `ln -s actual_file file_referencing_actual_file`

**Solution:**

`ln -s /flag ~/not-the-flag`<br>
`/challenge/catflag`
