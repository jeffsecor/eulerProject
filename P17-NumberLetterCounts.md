## Problem 17 - Number Letter Counts

This is a good question because it involves a few different coding elements. The question is basically, how many letters are there in all of the words for the numbers 1-1000?
On the one hand, you could figure out how many times the word "one" appears, and "two" and....and 'twenty", and ....and "one hundred"...If you go by this route, just
be sure to remember that each beginning of century does not have the word "and" i.e. 100 = 'one hundred' and 101 = one hundred and one"

The programming way is entertaining, although a bit cumbersome.  For each number, we determine the ones, tens, and hundred digit, and then
affix the appropriate text.  Then we can write a comprehension list to get all the numbers.  I found it was easiest to write a function for each digit place,
then write a final function for the entire word.  


for the ones place

```
def first(digit):
	if digit=='0':
		return ''
	elif digit=='1':
		return 'one'
	elif digit=='2':
		return 'two'
	elif digit=='3':
		return 'three'
	elif digit=='4':
		return 'four'
	elif digit=='5':
		return 'five'
	elif digit=='6':
		return 'six'
	elif digit=='7':
		return 'seven'
	elif digit=='8':
		return 'eight'
	elif digit=='9':
		return 'nine'
```

for the tens place (not the teens, that is a special case)

```
def second(digit):
	if digit=='2':
		return 'twenty'
	elif digit=='3':
		return 'thirty'
	elif digit=='4':
		return 'forty'
	elif digit=='5':
		return 'fifty'
	elif digit=='6':
		return 'sixty'
	elif digit=='7':
		return 'seventy'
	elif digit=='8':
		return 'eighty'
	elif digit=='9':
		return 'ninety'
	elif digit=='0':
		return ''
 ```


for the teens

```
 def teens(digit):
	if digit=='1':
		return 'eleven'
	elif digit=='2':
		return 'twelve'
	elif digit=='3':
		return 'thirteen'
	elif digit=='4':
		return 'fourteen'
	elif digit=='5':
		return 'fifteen'
	elif digit=='6':
		return 'sixteen'
	elif digit=='7':
		return 'seventeen'
	elif digit=='8':
		return 'eighteen'
	elif digit=='9':
		return 'nineteen'
	elif digit=='0':
		return 'ten'
```    


the hundreds case is easy, we just add the words "hundred and" to our existing function for ones and will strip the "and" where needed

```
def third(digit):
	return first(digit)+'hundredand'
```  


putting this all together now into a function
```
def word(number):
	text=''
	
  #make the number into a list to pick digit places
  num_list=list(str(number))
  
  #first take care of the teens special case, remember that python reads line by line in order
	if len(num_list)>1 and num_list[-2]=='1':
		text=teens(num_list[-1])
		if len(num_list)>2:
			text=third(num_list[-3])+text
		return text
	
  #if the number were a teen, the return would bring us out of this function. Otherwise, it carries on below
  
  digit=num_list[-1]
	text+=first(digit)
	if len(num_list)>1:
		text=second(num_list[-2])+text
	if len(num_list)>2:
		if num_list[-1]=='0' and num_list[-2]=='0':
			#this strips the "and" from the centennial beginning 
     			 text=third(num_list[-3])[:-3]+text
		else:
			 text=third(num_list[-3])+text
	return text
  ```
  Then using numpys array function and a list comprehension, wrapped in numpys cumsum
  
  ```
  np.cumsum(np.array([len(word(i)) for i in range(1,1000)]))
  ```
  
  The last element of this array is the number we need, and dont forget then to add the length for the word "onethousand" since that was not part of the code.
    
    
