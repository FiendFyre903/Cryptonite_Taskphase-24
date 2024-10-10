using the functions in the flag.c file, i substituted the word generated in the shell and got the corresponding little endian and big endian values.


```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <stdbool.h>
#include <ctype.h>
#include <time.h>

char *find_little_endian(const char *word)
{
    size_t word_len = strlen(word);
    char *little_endian = (char *)malloc((2 * word_len + 1) * sizeof(char));

    for (size_t i = word_len; i-- > 0;)
    {
        snprintf(&little_endian[(word_len - 1 - i) * 2], 3, "%02X", (unsigned char)word[i]);
    }

    little_endian[2 * word_len] = '\0';
    return little_endian;
}

char *find_big_endian(const char *word)
{
    size_t length = strlen(word);
    char *big_endian = (char *)malloc((2 * length + 1) * sizeof(char));

    for (size_t i = 0; i < length; i++)
    {
        snprintf(&big_endian[i * 2], 3, "%02X", (unsigned char)word[i]);
    }

    big_endian[2 * length] = '\0';
    return big_endian;
}


int main()
{
    char *challenge_word = "ihggj";
    printf("Word: %s\n", challenge_word);
    fflush(stdout);

    char *little_endian = find_little_endian(challenge_word);
    char *big_endian = find_big_endian(challenge_word);

    printf("%s\n", little_endian);
    printf("%s", big_endian);    


    return 0;
}
```

**Solution:**
```
fiendfyre@fedora:~/Downloads/PicoCTF$ nc titan.picoctf.net 58749
Welcome to the Endian CTF!
You need to find both the little endian and big endian representations of a word.
If you get both correct, you will receive the flag.
Word: ihggj
Enter the Little Endian representation: 6A67676869
Correct Little Endian representation!
Enter the Big Endian representation: 696867676A
Correct Big Endian representation!
Congratulations! You found both endian representations correctly!
Your Flag is: picoCTF{3ndi4n_sw4p_su33ess_91bc76a4}
```