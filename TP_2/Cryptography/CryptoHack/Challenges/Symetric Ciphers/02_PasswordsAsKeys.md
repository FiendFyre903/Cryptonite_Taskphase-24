## Passwords as Keys

### Flag - `crypto{k3y5__r__n07__p455w0rdz?}`

### Code

```python
from Crypto.Cipher import AES
import hashlib
from Crypto.Util.number import long_to_bytes

def decrypt(ciphertext, key):

    cipher = AES.new(key, AES.MODE_ECB)
    try:
        decrypted = cipher.decrypt(ciphertext)
    except ValueError as e:
        return 

    return decrypted.hex()

ciphertext =  bytes.fromhex("c92b7734070205bdf6c0087a751466ec13ae15e6f1bcdd3f3a535ec0f4bbae66")

with open("words.txt", "r") as f:
    words = [w.strip() for w in f.readlines()]

for word in words:
    key = hashlib.md5(word.encode()).digest()

    res = decrypt(ciphertext,key)

    decrypted = long_to_bytes(int(res,16))
    if b"crypto" in decrypted:
        print(decrypted)
```