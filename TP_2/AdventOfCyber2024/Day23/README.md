# DAY 23

We are given a hash and a hash-id.py program to identify the type of hash

using hash-id.py, the mts likely hash is SHA-256.

using john the ripper to crack the hash (using the rockyou worldlist), gives us the value. 

```john --format=raw-sha256 --rules=single --wordlist=wordlist.txt hash1.txt```

```SHA256$d956a72c83a895cb767bb5be8dba791395021dcece002b689cf3b5bf5aaa20ac:fluffycat12```


for the pdf, we need to convert it to a format john can work on.

using pdf2john.pl 

```pdf2john.pl private.pdf > private.john```

using the given wordlist since rockyou didnt work.

```john --rules=single --wordlist=wordlist.txt private.john```

which gives the password - ```M4y0rM41w4r3```

then i tried using qpdf but since user is not root, could not install it.

since we only want the text anyways, i used pdftotext to open the file.

```pdftotext private.pdf -upw M4y0rM41w4r3```

the flag was : ```THM{do_not_GET_CAUGHT}```



