# RSA Oracle

### Flag - `picoCTF{su((3ss_(r@ck1ng_r3@_92d53250}`

This was similar to No Padding No problem.

RSA when unpadded is homomorphic, which means the following two scenarios will give the same result:-

- If two encoded values are multiplied then decoded
- if two values are multiplied 

Using this , I encoded `2` using the n and e values provided and multiplied it with the ciphertext provided. The resulting product i entered in the prompt and got the decoded value.
his i divided by 2, and then convereted to binary to get the flag.


### Code

```python
from pwn import *

context.log_level='critical'
p = remote("titan.picoctf.net", 57879)

p.recvuntil(b"decrypt.")

with open("password.enc") as file:
    c = int(file.read())

p.sendline(b"E")
p.recvuntil(b"keysize): ")
p.sendline(b"\x02")
p.recvuntil(b"mod n) ")

c_a = int(p.recvline())

p.sendline(b"D")
p.recvuntil(b"decrypt: ")
p.sendline(str(c_a*c).encode())
p.recvuntil(b"mod n): ")

password = int(p.recvline(), 16) // 2
password = password.to_bytes(len(str(password))-7, "big").decode("utf-8")

print("Password:", password)
```