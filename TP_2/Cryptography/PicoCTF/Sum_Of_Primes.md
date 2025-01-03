# Sum-O-Primes

**Flag:** `picoCTF{pl33z_n0_g1v3_c0ngru3nc3_0f_5qu4r35_3921def5}`

- **step 1**

    This challenge gave us the value for `p+q` as well as `p*q`. This can be easily solved using the quadratic formula, or in this case, I used sympy's solver to solve it.

    Another difference was, instead of using Euler's Totient, instead a variable `m` was being used in its place, whose value was the LCM of `p-1` and `q-1`. 

    ```python
    from Crypto.Util.number import bytes_to_long, long_to_bytes
    from math import sqrt, lcm
    from sympy.solvers import solve
    from sympy import Symbol

    x = 0x152a1447b61d023bebab7b1f8bc9d934c2d4b0c8ef7e211dbbcf841136d030e3c829f222cec318f6f624eb529b54bcda848f65574896d70cd6c3460d0c9064cd66e826578c2035ab63da67d069fa302227a9012422d2402f8f0d4495ef66104ebd774f341aa62f493184301debf910ab3d1e72e357a99c460370254f3dfccd9ae
    n = 0x6fc1b2be753e8f480c8b7576f77d3063906a6a024fe954d7fd01545e8f5b6becc24d70e9a5bc034a4c00e61f8a6176feb7d35fe39c8c03617ea4552840d93aa09469716913b58df677c785cd7633d1b7d31e2222cab53be235aa412ac5c5b07b500cf3fd5d6b91e2ddc51bff1e6eec2cb68723af668df36e10e332a9cbb7f3e2df9593fa0e553ed58afec2aa3bc4ae8ef1140e4779f61bdeae4c0b46136294cf151622e83c3d71b97c815b542208baa28207225f134c5a4feac998aeb178a5552f08643717819c10e8b5ec7715696c3bf4434fbea8e8a516dfd90046a999e24a0fb10d27291eb29ef3f285149c20189e7d0190417991094948180196543b8c91
    c = 0x16acf84a73cefd321ed491a15c640a495b09050cdce435ec37442faf9a694775e1ebffb6dbad6133cbc54e3f641506b0613f711625594fcb467f915f2708714b4c9936f5f4752c3299157cff4eb68eb82c0054dae351314829974f4feadaf126cda92b97e348dbef2640ec3a729a064e615df73d644700f93bf87579683e253d29622525bea3644f59aac8e0b2553bfea48d99e9b323e03cbf55166659974eb8c51cc7b2c2c5d6aa6c01b056a8ed7283d96656a3496f266726605af1be139d586f208d4d7c59c2771dc8036d490d3672ee4513301002775d7c39eac421c6cb4f01344e061549a4cb11c057accef1726572e447501004c772ec91b4a55811280f

    e = 65537

    # p + q = x
    # p * q = n
    # p = x - q
    # q * (x-q) = n
    # q^2 = q*x - n
    # q^2 - q*x +n = 0
    # q = x +- sqrt(x^2 - 4 * n) / 2 * a

    a = Symbol('a')
    b = Symbol('b')

    answer = solve([a+b-x, a*b-n],a,b)

    p = int(answer[0][0])
    q = int(answer[0][1])

    m = lcm(p - 1, q - 1)
    d = pow(e, -1, m)

    flag = pow(c,d,n)

    print(long_to_bytes(flag))
    ```

**What I learned:**

1. How to use Sympy solver for basic equations.

**Other incorrect methods I tried:**

- I first tried using quadratic formula to solve but ran into an error - `OverflowError: int too large to convert to float` as the integer value was too high. 

**References**

- https://docs.sympy.org/latest/modules/solvers/solvers.html
