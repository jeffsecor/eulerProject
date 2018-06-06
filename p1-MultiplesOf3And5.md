# Project Euler
##Challenge 1 - Multiples of 3 and 5

This is a simple problem to start the coding challenge.  The main concept is to use the modulo operator.  The elegant solution is 
```
print(sum([x for x in range(1,1000) if x%3==0 or x%5 == 0 ]))

```
