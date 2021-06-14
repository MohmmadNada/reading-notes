# List Comprehensions in Python
you can put in all kinds of objects in lists.
The list comprehension always returns a result list.

```
new_list = []
for i in old_list:
    if filter(i):
        new_list.append(expressions(i))
```
The basic syntax uses square brackets.
```
[ expression(item ) for item in list if conditional ]
```
This is equivalent to:

```
for item in list:
    if conditional:
        expression
```
## Examples
1. Create a simple list
```
x = [i for i in range(10)]
print x

#This will give the output:
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
```
2. Create a list using loops and list comprehension
list of squares. Start with an empty list.
```
# You can either use loops:
squares = []

for x in range(10):
    squares.append(x**2)
 
print squares
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]

# Or you can use list comprehensions to get the same result:
squares = [x**2 for x in range(10)]

print squares
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
```
3. Show the first letter of each word
```
listOfWords = ["this","is","a","list","of","words"]

items = [ word[0] for word in listOfWords ]

print items
```
> remeber: x.isdigit() , true if number x.isalpha()  true no number
4. Parsing a file using list comprehension
Create a text file and put in some text in it.

this is line1
this is line2
this is line3
this is line4
this is line5

Save the file as test.txt
```
# Then create the filter by using list comprehension:

fh = open("test.txt", "r")

result = [i for i in fh if "line3" in i]

print result
```
> Output: [‘this is line3‘]

4. Using list comprehension in functions
```
# Create a function and name it double:
def double(x):
  return x*2

# If you now just print that function with a value in it, it should look like this:
>>> print double(10)
20
```
We can easily use list comprehension on that function.

```
>>> [double(x) for x in range(10)]

print double
[0, 2, 4, 6, 8, 10, 12, 14, 16, 18]

# You can put in conditions:

>>> [double(x) for x in range(10) if x%2==0]
[0, 4, 8, 12, 16]

# You can add more arguments:

>>> [x+y for x in [10,30,50] for y in [20,40,60]]
[30, 50, 70, 50, 70, 90, 70, 90, 110]
```

Resources:
* [List Comprehensions](https://www.pythonforbeginners.com/basics/list-comprehensions-in-python)
* [Primer on Decorators](https://realpython.com/primer-on-python-decorators/)
* [Debugging with PySnooper](https://www.pythonpodcast.com/pysnooper-python-debugging-episode-241/)