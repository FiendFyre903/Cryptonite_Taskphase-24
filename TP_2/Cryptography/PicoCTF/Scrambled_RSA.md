# Scrambled RSA

**Flag:** `picoCTF{bad_1d3a5_2268684}`

- **step 1**

    The challenge was taking each character and encrypting it and then shuffling it.

    E(a) was in E(ab)

    E(ab) was in E(abc)

    basically we can add one character, encode it using the server, then check if it is a part of flag. If it is, append it to the decrypted_flag and then try the same thing again to find the next letter until reaching `}`.

    To optimise the code so it ran fast enough to finish before the serve timed out, I places the more common characters in the start of the characters string.

    Also, known stored known encryptions and anything in known was removed from enc to prevent redundant checks.

    flag was also updated everytime a letter was found and the decrypted section was removed so it kept getting smaller to prevent redundant checks once again.


    ```python
    from pwn import *

    chars = r"CTF{}_134abcdpioefghjklmnqrstuvwxyz2567890"

    df = ''
    known = []
    r = remote("mercury.picoctf.net", 6276)
    f = r.recvline(keepends=False).decode()[6:]
    r.recvline()
    r.recvline()

    while '}' not in df:
        for i in chars:
            pl = df+i
            r.sendafter("me: ", pl+"\n")
            enc = r.recvline(keepends=False).decode().split("Here you go: ")[1]
            for x in known:
                enc = enc.replace(x, '')
            if(enc in f):
                f = f.replace(enc, '')
                known.append(enc)
                df += i
                print(df)
                break
    ```
    


**What I learned:**

1. How to use pwn module to interact with a url/server

**Other incorrect methods I tried:**

- Lots of random attempts with differnt combinations to try and find a pattern, but no success except for the one used to find the answer.

**References**

- https://discuss.python.org/t/trying-to-interact-with-a-remote-console-using-pwntools/15561