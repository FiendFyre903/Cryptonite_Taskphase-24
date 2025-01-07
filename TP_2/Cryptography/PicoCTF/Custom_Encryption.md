## Custom Encryption

### Flag - `picoCTF{custom_d2cr0pt6d_019c831c}`

### Code

```python
# from random import randint

# def encrypt(plaintext, key):
#     cipher = []
#     for char in plaintext:
#         cipher.append(((ord(char) * key*311)))
#     return cipher

def dynamic_xor_encrypt(plaintext, text_key):
    cipher_text = ""
    key_length = len(text_key)
    for i, char in enumerate(plaintext[::-1]):
        key_char = text_key[i % key_length]
        encrypted_char = chr(ord(char) ^ ord(key_char))
        cipher_text += encrypted_char
    return cipher_text


def dynamic_xor_decrypt(plaintext, text_key):
    cipher_text = ""
    key_length = len(text_key)
    for i, char in enumerate(plaintext):
        key_char = text_key[i % key_length]
        encrypted_char = chr(ord(char) ^ ord(key_char))
        cipher_text += encrypted_char
    return cipher_text[::-1]

# def test(plain_text, text_key):
#     p = 97
#     g = 31
#     if not is_prime(p) and not is_prime(g):
#         print("Enter prime numbers")
#         return
#     a = randint(p-10, p)
#     b = randint(g-10, g)
#     print(f"a = {a}")
#     print(f"b = {b}")
#     u = pow(g, a, p)
#     v = pow(g, b, p)
#     key = pow(v, a, p)
#     b_key = pow(u, b, p)
#     shared_key = None
#     if key == b_key:
#         shared_key = key
#     else:
#         print("Invalid key")
#         return
#     semi_cipher = dynamic_xor_encrypt(plain_text, text_key)
#     cipher = encrypt(semi_cipher, shared_key)
#     print(f'cipher is: {cipher}')


# if __name__ == "__main__":
#     message = sys.argv[1]
#     test(message, "trudeau")

a = 88
b = 26
cipher = [97965, 185045, 740180, 946995, 1012305, 21770, 827260, 751065, 718410, 457170, 0, 903455, 228585, 54425, 740180, 0, 239470, 936110, 10885, 674870, 261240, 293895, 65310, 65310, 185045, 65310, 283010, 555135, 348320, 533365, 283010, 76195, 130620, 185045]


def decrypt(cipher,a,b):
    text_key = "trudeau"
    p = 97
    g = 31
    v = pow(g,b,p)
    key = pow(v,a,p)

    semi_decrypt = ""

    for i in range(len(cipher)):
        semi_decrypt += chr(cipher[i] // (311 * key))

    print(semi_decrypt)

    semi_decrypted = dynamic_xor_decrypt(semi_decrypt,text_key)

    return semi_decrypted

print(decrypt(cipher,a,b))
```