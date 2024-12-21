# Export Grade

**Flag:** `crypto{9467,2742}`

- **step 1**

    Using the algorithm given, I wrote the following python script to calculate [7863]P.

    ```python
    from Crypto.Util.number import *

    def addition(x,y):
        p = 9739
        a = 497
        b = 1768
        if x == [0,0]:
            return y 
        elif y == [0,0]:
            return x 
        elif x[0] == y[0] and x[1] == -y[1]:
            return [0,0]
        else:
            if x == y:
                Lambda = (3 * x[0]**2 + a) * inverse((2 * x[1]),p)
            else:
                Lambda = (y[1]-x[1] ) * inverse((y[0]-x[0]),p)
            x3 = pow(Lambda,2) - (x[0] + y[0])
            y3 = Lambda*(x[0] - x3) - x[1]

            return [x3%p,y3%p]

    def multiply(P,n):
        p = 9739
        a = 497
        b = 1768
        Q = P
        R = [0,0]
        while(n>0):
            if n%2 == 1:
                R = addition(R,Q)
            Q = addition(Q,Q)
            n = n//2
        return R

    P = [2339,2213]

    print(multiply(P,7863))
    ```    

**What I learned:**

1. Basics of Elliptic Curve Cryptography in a field p

**Other incorrect methods I tried:**

- None

**References**

- None