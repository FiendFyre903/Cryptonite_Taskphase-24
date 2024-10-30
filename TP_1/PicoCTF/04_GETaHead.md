
Using `curl` to view the header gives the flag.

`curl -I URL`

**Solution**

```
fiendfyre@fedora:~$ man curl
fiendfyre@fedora:~$ curl -I http://mercury.picoctf.net:28916/
HTTP/1.1 200 OK
flag: picoCTF{r3j3ct_th3_du4l1ty_70bc61c4}
Content-type: text/html; charset=UTF-8
```