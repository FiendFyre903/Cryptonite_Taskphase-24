## ECB Oracle

### Flag - `crypto{p3n6u1n5_h473_3cb}`

### Code

```py
from Crypto.Util.number import long_to_bytes

import requests
import time

url = "https://aes.cryptohack.org/ecb_oracle/encrypt/"

chars = r'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789_-~!?#%&@{}'

last_found_character = None
i = 0

flag = ''

while(last_found_character!='}'):
    plaintext = ('1'*(31-i))
    response = requests.get(f"{url}{plaintext.encode().hex()}/")
    a = response.json()['ciphertext'][32:64]
    for char in chars:
        response = requests.get(f"{url}{plaintext.encode().hex()}{flag.encode().hex()}{char.encode().hex()}/")
        b = response.json()['ciphertext'][32:64]
        if a == b:
            flag += char
            last_found_character = char
            break   
    i+=1
    print(flag)

print(flag)
```