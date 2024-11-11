# Vault door 7

**Flag:** `picoCTF{A_b1t_0f_b1t_sh1fTiNg_702640db5a}`

- **step 1**

    This challenge used bitwise shift to combine 4 characters into one int. this was accomplished by converting each character to 8 bits and then concatenating them(effectively) to get one binary that was converted into an int.

    ```python
    from Crypto.Util.number import long2str

    x = [1096770097,1952395366,1600270708,1601398833,1716808014,1734293296,842413104,1684157793]

    flag = []

    for a in x:
        flag.append(a >> 24)
        flag.append((a >> 16)% 2**8)
        flag.append((a >> 8)% 2**8)
        flag.append(a % 2**8)

    for a in flag:
            print(str(long2str(a))[2], end="")
    ```


**What I learned:**

1. How bit-shifting works and how to extract specific parts of a binary number

**Other incorrect methods I tried:**

- None

**References**

- None



