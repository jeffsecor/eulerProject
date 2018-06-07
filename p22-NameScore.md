# Problem 22 - Name Score
This problem imports a 46k file of first names.  The task is to compute a numerical score for each name based on the position of each letter in the alphabet,
then sum the score of all the names.Then this score is multiplied by the position of the name in the alphabetically ordered list.
This is done in a few logical steps, though a single list compreshension could probably be done with python.

First we open, read, and then split the file across each comma to put the names into a list, then sort the list
```
a=open('names.txt','r')
b=a.read().split(',')
a.close
b.sort()
```
To compute the values, we go through each name in the list, then each letter in the name, then add the value to the name score.  As per the directions,
this value is then multiplied by the index.
```
value = 0
index=1
for name in b:
    namescore=0
    for l in list(name):
        if ord(l)-64>0:
            namescore+=(ord(l)-64)
    value+=namescore*index
    index+=1
print(value)
```
