# Vault door 5

**Flag:** `c0nv3rt1ng_fr0m_ba5e_64_e3152bf4`


- **step 1**

    The program first used url encoding and then base64 encoding. I wrote a simple python script to first decode it from base64 and then url-decode to get the flag.

    ```python
    import base64
    from urllib.parse import unquote

    str1 = "JTYzJTMwJTZlJTc2JTMzJTcyJTc0JTMxJTZlJTY3JTVm"+ "JTY2JTcyJTMwJTZkJTVmJTYyJTYxJTM1JTY1JTVmJTM2"+ "JTM0JTVmJTY1JTMzJTMxJTM1JTMyJTYyJTY2JTM0"


    b64decoded = base64.b64decode(str1)

    urldecoded = unquote(b64decoded)

    print(urldecoded)
    ```

**What I learned:**

1. None

**Other incorrect methods I tried:**

- None

**References**

- None



