# No padding, no problem

**Flag:** `picoCTF{m4yb3_Th0se_m3s54g3s_4r3_difurrent_5814368}`

- **step 1**

    RSA when unpadded is homomorphic, which means the following two scenarios will give the same result:-

    - If two encoded values are multiplied then decoded
    - if two values are multiplied 

    Using this , I encoded `2` using the n and e values provided and multiplied it with the ciphertext provided. The resulting product i entered in the prompt and got the decoded value.
    This i divided by 2, and then convereted to binary to get the flag.


**What I learned:**

1. RSA is homomorphic when unpadded

**Other incorrect methods I tried:**

- I tried padding with zeros at the start but the program recognised and rejected that.

**References**

- None