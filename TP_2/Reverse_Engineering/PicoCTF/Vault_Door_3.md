# Vault door 1

**Flag:** `picoCTF{jU5t_a_s1mpl3_an4gr4m_4_u_1fb380}`



- **step 1**

    This time the flag was anagrammed, i wrote another function that did the exact opposite of the checkPassword func.

    ```java
    public static String pass(String buffer) {
        char[] password = new char[32];
        int i;
        for (i=0; i<8; i++) {
            password[i] = buffer.charAt(i);
        }
        for (i=8; i<16; i++) {
            password[23-i] = buffer.charAt(i);
        }
        for (i=16; i<32; i+=2) {
            password[46-i] = buffer.charAt(i);
        }
        for (i=31; i>=17; i-=2) {
            password[i] = buffer.charAt(i);
        }
        String s = new String(password);
        return s;
    }
    ```

**What I learned:**

1. None

**Other incorrect methods I tried:**

- None

**References**

- None