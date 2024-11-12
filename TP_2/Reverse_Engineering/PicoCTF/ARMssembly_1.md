# ARMssembly 1

**Flag:** `picoCTF{000000E8}`

- **step 1**

    Similar to the previous challenge, this one performed 3 operations

    Take 3 inputs <br>
    x = 87 <br>
    y = 3 <br>
    z = 3 <br>

    1. Shift x(87) left by y(3) bits -> 696
    2. Divides 696 by z(3) -> 232
    3. Now it subtracts the input from 232

    We want the result to be zero, therefore the input needs to be 232 which in hex is E8.

**What I learned:**

1. None

**Other incorrect methods I tried:**

- None

**References**

- None