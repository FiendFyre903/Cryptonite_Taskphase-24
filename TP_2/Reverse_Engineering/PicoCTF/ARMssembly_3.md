# ARMssembly 3

**Flag:** `picoCTF{0000003f}`

- **step 1**

    Similar to the previous questions I analysed the assembly and made an equivalent python program as it was too lengthy to manuallycalculate this time.

    ```python
    def func(val):
    result = 0
    while val != 0:
        if val & 1:  
            result += 3
        val >>= 1  
    return result

    print(func(4012702611))  
    ```

    this gave the result 63 which is 0000003f

**What I learned:**

1. None

**Other incorrect methods I tried:**

- Instead of figuring out the assembly like previous challenges, i decided to retry running the script itself. but i had errors because some necessary libraries were not found by dnf.

**References**

- https://github.com/joebobmiles/ARMv8ViaLinuxCommandline