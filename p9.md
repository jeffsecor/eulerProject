## Problem 9 Special Pythagorean triplet

Find the product of the three numbers in the pythagorean triplet that sum to 1000.  For this we can run a while loop where the upper limit is 999, since the other
numbers in the pythagorean triplet must be included.  Once we find our answer, we can exit the loop, so we use a break.  

To test for a pythagorean triplet, test if a^2+b^2 % 1 = 0, i.e. it is an integer and therefore the numbers form a triplet.  Then test if the sum
is 1000.  If so, we break out of the loop
```
import math
done = False
while not done:
    for a in range(999):
        for b in range(999):
            if math.sqrt(a**2+b**2)%1==0 and a+b+math.sqrt(a**2+b**2)==1000:
                print(a*b*math.sqrt(a**2+b**2))
                done = True
                break    
```
