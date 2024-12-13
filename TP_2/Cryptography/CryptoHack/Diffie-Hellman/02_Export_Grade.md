# Export Grade

**Flag:** `crypto{d0wn6r4d35_4r3_d4n63r0u5}`

- **step 1**

    I selected the smallest Key size DH64 as that will be the easiest to brute force.


- **step 2**

    I used the discrete_log function of sage and used that to bruteforce a which I used to get the key and then decrypted the flag.
    
    ```python
    from sage.groups.generic import discrete_log
    from sage.arith.misc import power_mod
    from Crypto.Cipher import AES
    from Crypto.Util.Padding import unpad
    import hashlib
    from sage.all import Mod

    def is_pkcs7_padded(message):
        padding = message[-message[-1]:]
        return all(padding[i] == len(padding) for i in range(0, len(padding)))


    def decrypt_flag(shared_secret: int, iv: str, ciphertext: str):
        # Derive AES key from shared secret
        sha1 = hashlib.sha1()
        sha1.update(str(shared_secret).encode('ascii'))
        key = sha1.digest()[:16]
        # Decrypt flag
        ciphertext = bytes.fromhex(ciphertext)
        iv = bytes.fromhex(iv)
        cipher = AES.new(key, AES.MODE_CBC, iv)
        plaintext = cipher.decrypt(ciphertext)
        if is_pkcs7_padded(plaintext):
            return unpad(plaintext, 16).decode('ascii')
        else:
            return plaintext.decode('ascii')

    p = int("0xde26ab651b92a129",16)
    g = Mod(2, p)
    A = Mod(int("0xc2a25a3f20e5f246",16), p)
    B = int("0x1781817d01fa74ef",16)
    iv = "b0410912d9d2b151bfa0fbe23d44698b"
    encrypted_flag = "e7c4a562425968bb09af60d68aa25b5fb8d985644d1c17d927814d71f9f83d5c"

    a = discrete_log(A, g)
    shared_secret = int(power_mod(B, a, p))
    print(decrypt_flag(shared_secret, iv, encrypted_flag))
    ```


**What I learned:**

1. RSA is homomorphic when unpadded

**Other incorrect methods I tried:**

- Bruteforcing values of a by trying every pow(g,a,p). It took too long

    ```python
    from sympy.ntheory import factorint

    {"p": "0xde26ab651b92a129", "g": "0x2", "A": "0xc2a25a3f20e5f246"}
    {"B": "0x1781817d01fa74ef"}
    {"iv": "b0410912d9d2b151bfa0fbe23d44698b", "encrypted_flag": "e7c4a562425968bb09af60d68aa25b5fb8d985644d1c17d927814d71f9f83d5c"}

    p = int("0xde26ab651b92a129",16)
    g = 2
    A = int("0xc2a25a3f20e5f246",16)
    B = int("0x1781817d01fa74ef",16)

    k = 1
    i = 1
    def brute(i):
        while(True):
            if(pow(g,i,p)==A):
                return i
            i+=1
            print(i)

    a = brute(i)
    print(a)
    ```

- Baby-Step Big-step Algorithm. Filled up disk very fast

**References**

- None