# spelling quiz

**Flag:** `picoCTF{perhaps_the_dog_jumped_over_was_just_tired}`



- **step 1**

    Understanding the python program and how it interacts with the two text files.

    Purpose of both text files.

    Aim is to reverse whatever the encrypt script does.
    
    It is a substitution cipher. The study guide is a huge set of words to help crack the cipher.

- **step 2**

    I used an online substitution solver and using just the top 200 words in the study guide, it gave an accurate mapping. 
    
    Using that and a simple python scrypt i decoded the flag.txt file and got the flag.

    Script:

    ```python
    filename ='./public/study-guide.txt'

    text = open(filename, 'r').read()
    flag = open('./public/flag.txt', 'r').read()
    flag_list = list(flag)

    key = dict(zip(list("abcdefghijklmnopqrstuvwxyz"),list("sprgwhkjoqzldcuvyemnbtiafx")))

    for i in range(len(flag_list)):
        if flag_list[i] in key:
            flag_list[i] = key[flag_list[i]]

    print("".join(flag_list))
    ```


**What I learned:**

1. Learned the basics of how a substitution cipher works. The concept of letter frequency and how that could be used to solve such a cipher. 
2. Basic python scripting and file handling. Particulalry, how to sort dictionaries based on values rather than keys.

**Other incorrect methods I tried:**

- I first tried letter frequency analysis to break the substitution cipher using an online ranking. This did not give any meaningful output.

    The code I used:-

    ```python
    filename ='./public/study-guide.txt'
    freq_order = list("etaoinshrdlcumwfgypbvkjxqz")
    print(len(freq_order))

    text = open(filename, 'r').read()
    flag = open('./public/flag.txt', "r").read()

    dictionary = dict(zip(list("abcdefghijklmnopqrstuvwxyz"),[0]*26))


    for y in text:
        for x in y:
            if x in dictionary:
                dictionary[x] = dictionary[x] + 1

    print(dictionary)
    sorted_items = sorted(dictionary.items(), key=lambda kv: (kv[1], kv[0]), reverse=True)


    list2 = [ x[0] for x in sorted_items]
    print(list2)
        
    key = dict(zip(list2,freq_order))
    print(key)

    flag_list = list(flag)

    for i in range(len(flag_list)):
    if flag_list[i] in key:
        flag_list[i] = key[flag_list[i]]

    print("".join(flag_list))
    ```

References

- [Letter frequency](https://www3.nd.edu/~busiforc/handouts/cryptography/letterfrequencies.html)
- [Substitution Solver](https://www.guballa.de/substitution-solver)
- [OS module tutorial](https://www.geeksforgeeks.org/python-os-path-join-method/)
