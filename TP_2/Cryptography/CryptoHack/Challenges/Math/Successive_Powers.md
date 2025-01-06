```python
from Crypto.Util.number import *

ls = [588,665,216,113,642,4,836,114,851,492,819,237]

for p in range(852,1000):
    try:
        x = [(ls[i] * pow(ls[i-1],-1,p))%p for i in range(1,len(ls))]
        if(len(set(x))==1):
            print(f"x: {x[0]}, p: {p}")
    except:
        pass
```