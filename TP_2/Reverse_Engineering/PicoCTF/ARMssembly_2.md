# ARMssembly 2

**Flag:** `picoCTF{ed2c0662}`

- **step 1**

    This time the function basically calls itself continuosly creating a loop

    in simple terms it has 3 variables and one loop

    ```python
    Input = 4189673334

    counter = 0

    value = 0

    while (counter < input):
        counter++
        value +=3

    ```

    which means the value that is finally returned is 3 * Input

    here 3*4189673334 = 2ED2C0662 in hex but this is 9 digits long, therefore i simply removed the MSB and took the rest 8.


**What I learned:**

1. wzr stores 0, its a quick way to get 0
2. how to convert a hex to 32 bits

**Other incorrect methods I tried:**

- Tried lots of different python functions that converted integers to 32-bit format, but its impossible to convert 36 bits to 32 without losing data.

**References**

- None