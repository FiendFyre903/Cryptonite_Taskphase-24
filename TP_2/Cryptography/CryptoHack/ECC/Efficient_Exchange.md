# Efficient Exchange

**Flag:** `crypto{3ff1c1ent_k3y_3xch4ng3}`

- **step 1**

    We had to get y from x, so I used the formula for elliptic curves to get both possibilities.

    ```python
    def sqrt(x, q):
    for i in range(1, q):
        if pow(i,2,q) == x:
            return (i, q - i)
    return None

    # finding y

    x = 4726

    y1,y2 = sqrt((x**3 + 497*x + 1768)% 9739,9739) 

    X1 = [x,y1]
    X2 = [x,y2]
    S = multiply(X1,6534)
    print(S)
    S = multiply(X2,6534)
    print(S)
    ``` 

    This gave me an x(S) of 1791 which I used as the secret in the decrypt program and that gave me the flag.

**What I learned:**

1. How to calculate root in a field

**Other incorrect methods I tried:**

- None

**References**

- None