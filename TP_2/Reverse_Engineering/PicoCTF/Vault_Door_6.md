# Vault door 6

**Flag:** `picoCTF{n0t_mUcH_h4rD3r_tH4n_x0r_95be5dc}`


- **step 1**

    This vault used XOR encryption, so i just XOR'ed it again with the same number and got the original flag.

    ```python
    from Crypto.Util.number import long2str

    ls = [
            0x3b, 0x65, 0x21, 0xa , 0x38, 0x0 , 0x36, 0x1d,
            0xa , 0x3d, 0x61, 0x27, 0x11, 0x66, 0x27, 0xa ,
            0x21, 0x1d, 0x61, 0x3b, 0xa , 0x2d, 0x65, 0x27,
            0xa , 0x6c, 0x60, 0x37, 0x30, 0x60, 0x31, 0x36,
        ]

    decodedls = [x ^ 0x55 for x in ls]

    print(decodedls)

    for x in decodedls:
        print(str(long2str(x))[2], end="")
    ```

    

**What I learned:**

1. None

**Other incorrect methods I tried:**

- None

**References**

- None



