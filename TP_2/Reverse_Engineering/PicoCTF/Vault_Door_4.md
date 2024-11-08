# Vault door 4

**Flag:** `jU5t_4_bUnCh_0f_bYt3s_f4a8cd8f7e`


- **step 1**

    The following code snippet converted the bytes back to string by first converting each one to a character and then appending to the string.

    ```java
    byte[] bytes = {
            106 , 85  , 53  , 116 , 95  , 52  , 95  , 98  ,
            0x55, 0x6e, 0x43, 0x68, 0x5f, 0x30, 0x66, 0x5f,
            0142, 0131, 0164, 063 , 0163, 0137, 0146, 064 ,
            'a' , '8' , 'c' , 'd' , '8' , 'f' , '7' , 'e' ,
        };

        String str = "";

        for(int i = 0; i < bytes.length; i++)
            str += (char)bytes[i];
        
        System.out.println(str);
    ```

**What I learned:**

1. Prefixing a number with a `0` in java makes it octal (base 8). 

**Other incorrect methods I tried:**

- None

**References**

- None



