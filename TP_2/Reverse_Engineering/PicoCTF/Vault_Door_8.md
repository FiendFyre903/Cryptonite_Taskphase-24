# Vault door 7

**Flag:** `picoCTF{s0m3_m0r3_b1t_sh1fTiNg_91c642112}`

- **step 1**

    This vault program swapped bits of each individual character in a specific order.

    To reverse this i just reversed the order of swapping.

    ```java
    import java.util.*;

    class VaultDoor8 {
        public static void main(String args[]) {
            char[] scrambled = {
                0xF4, 0xC0, 0x97, 0xF0, 0x77, 0x97, 0xC0, 0xE4, 0xF0, 0x77, 0xA4, 0xD0, 0xC5, 0x77, 0xF4, 0x86, 0xD0,
                0xA5, 0x45, 0x96, 0x27, 0xB5, 0x77, 0xD2, 0xD0, 0xB4, 0xE1, 0xC1, 0xE0, 0xD0, 0xD0, 0xE0 };

            char[] flag = unscramble(scrambled);

            for(int i = 0;i<flag.length;i++){
                System.out.print(flag[i]);
            }
        }
            
        public static char[] unscramble(char[] password) {
            char[] a = password;
            for (int b = 0; b < a.length; b++) {
                char c = a[b];
                c = switchBits(c, 6, 7);
                c = switchBits(c, 2, 5);
                c = switchBits(c, 3, 4);
                c = switchBits(c, 0, 1);
                c = switchBits(c, 4, 7);
                c = switchBits(c, 5, 6);
                c = switchBits(c, 0, 3);
                c = switchBits(c, 1, 2);
                a[b] = c;
            }
            return a;
        }

        public static char switchBits(char c, int p1, int p2) {
            char mask1 = (char) (1 << p1);
            char mask2 = (char) (1 << p2);
            char bit1 = (char) (c & mask1);
            char bit2 = (char) (c & mask2);
            char rest = (char) (c & ~(mask1 | mask2));
            char shift = (char) (p2 - p1);
            char result = (char) ((bit1 << shift) | (bit2 >> shift) | rest);
            return result;
        }
    }
    ```


**What I learned:**

1. None

**Other incorrect methods I tried:**

- None

**References**

- None



