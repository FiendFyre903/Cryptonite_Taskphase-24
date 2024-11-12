# ARMssembly 4

**Flag:** `picoCTF{4874BF71}`

- **step 1**

    This assembly program is veryy long but in reality most of it is not necessary since our input (1215610622) is soo big, we can just follow the code to the functions we actually need.

    1. func1 adds 100 and passes it on to func2 (since input>100).
    
        1215610622 + 100 = 1215610722

    2. func2 adds 13 and passes it on to func5(since input >499).

        1215610722 + 13 = 1215610735

    3. func5 just calls func8 with no changes

    4. func8 adds to and returns it.

        1215610735 + 2 = 1215610737


    1215610737 in hex is 4874BF71 

    This way, I only had to spend time figuring out the functions that were actually needed, skipping the rest.


**What I learned:**

1. None

**Other incorrect methods I tried:**

- None

**References**

- None