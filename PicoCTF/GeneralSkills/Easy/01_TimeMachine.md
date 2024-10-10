As the description implied, the flag was hidden in the git folder in a file which had the word `commit` in its name.


**Solution:**
```
fiendfyre@fedora:~/Downloads/PicoCTF/challenge$ ls
drop-in
fiendfyre@fedora:~/Downloads/PicoCTF/challenge$ cd dr*
fiendfyre@fedora:~/Downloads/PicoCTF/challenge/drop-in$ ls
message.txt
fiendfyre@fedora:~/Downloads/PicoCTF/challenge/drop-in$ ls -a
.  ..  .git  message.txt
fiendfyre@fedora:~/Downloads/PicoCTF/challenge/drop-in$ cat .git
cat: .git: Is a directory
fiendfyre@fedora:~/Downloads/PicoCTF/challenge/drop-in$ cd .git
fiendfyre@fedora:~/Downloads/PicoCTF/challenge/drop-in/.git$ ls
branches  COMMIT_EDITMSG  config  description  HEAD  hooks  index  info  logs  objects  refs
fiendfyre@fedora:~/Downloads/PicoCTF/challenge/drop-in/.git$ cat COMM*
picoCTF{t1m3m@ch1n3_d3161c0f}
fiendfyre@fedora:~/Downloads/PicoCTF/challenge/drop-in/.git$ 
```

FLAG - `picoCTF{t1m3m@ch1n3_d3161c0f}`