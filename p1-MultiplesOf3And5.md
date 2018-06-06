# Project Euler Challenge 1
## Multiples of 3 and 5
### -Python-

This is a simple problem to start the coding challenge.  The main concept is to use the modulo operator, and that variable comparison uses double equal signs.  An one line solution using a python _"list comprehension"_  is 
```
print(sum([x for x in range(1,1000) if x%3==0 or x%5==0 ]))

```

An oldschool, but more explicit solution uses variable declaration and a while loop.  
```
x,total = 0,0
while x<1000:
    if x%3==0 or x%5==0:
        total+=x
    x+=1
print(total)
```
