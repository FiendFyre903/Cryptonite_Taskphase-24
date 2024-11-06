# SRA

**Flag:** `picoCTF{7h053_51n5_4r3_n0_m0r3_38268294}`



- **step 1**

    Analysing the `chal.py` program let me know the following details:

    - The program gives us `ct` and `d`(thats what gets printed)
    - e is 65537
    - p and q are each 128 bits

- **step 2**

    Using the following python script to bruteforce decode the possible solutions.

    Formula `(p-1) * (q-1) * k = e * d - 1`

    - Using 

    ```python
    from Crypto.Util.number import bytes_to_long, long_to_bytes
    import math
    from itertools import combinations, permutations
    from primefac import isprime
    import string

    e = 65537
    ct = 61049145037735743596950152094536969671970385393990490616464138725965087296489
    d = 21938323223722389048601083616481213308967345294511864304206793201983273931217

    # (p-1) * (q-1) * k = e*d - 1

    num = e*d -1

    print(num)
    str = input("Enter factors: ") # use website to get factors as its faster

    prime_factors = str.split(", ")

    for i in range(len(prime_factors)):
        prime_factors[i] = int(prime_factors[i])

    factors = set()

    for r in range(1, len(prime_factors)+1):
        for comb in combinations(prime_factors,r):
            factors.add(math.prod(comb))


    # checking to ensure p, q are primes and of length 128.
    primes = set()

    for factor in factors:
        if isprime(factor+1) and (factor + 1).bit_length()==128:
            primes.add(factor)


    subsets = list(combinations(primes, 2))

    for subset in subsets:
        n = (subset[0]+1) * (subset[1] + 1)
        pt = long_to_bytes(pow(ct,d,n))

        try:
            pt = pt.decode('ascii')
        except UnicodeDecodeError:
            continue
        print(pt)
    ```


**What I learned:**

1. How to use some functions of itertool and crypto python libraries


**Other incorrect methods I tried:**

- None

**References**

- https://www.alpertron.com.ar/ECM.HTM (fast calculator for large numbers)