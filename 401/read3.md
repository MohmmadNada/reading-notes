# Readings: FileIO & Exceptions

## Reading and Writing Files in Python (Guide)

#### What Is a File?
a file is a contiguous set of bytes used to store data.
these byte files are then translated into binary 1 and 0 for easier processing by the computer..

three main parts in file :
* Header:(file name, size, type, and so on)
* Data: written by the creator
* End of file (EOF):special character that indicates the end of the file

#### Line Endings

Windows uses the CR+LF characters to indicate a new line, while Unix and the newer Mac versions use just the LF character. 

unix :
```  
German Shepherd\r
\n
```` 
Opening and Closing a File in Python
let`s explain it by code example : 
1. open 
``` 
file = open('dog_breeds.txt')
do any coding between
finally:
    file.close()
````
or
``` 
with open('dog_breeds.txt') as reader:
    # Further file processing goes here
````
The with statement automatically takes care of closing the file once it leaves the with block,

> Warning: You should always make sure that an open file is properly closed.

what we want from file , r-read ,wirte ... etc we can add as argument 

```
with open('dog_breeds.txt', 'r') as reader:
    # Further file processing goes here
```
| Lab Character       | Meaning |
| ----------- | ----------- |
| 'r'    | Open for reading (default)|
| 'w'     | Open for writing, truncating (overwriting) the file first|
| 'rb' or 'wb'     | 	Open in binary mode (read/write using byte data)|
	
	
#### Reading and Writing Opened Files

methods to help you out:
|Method|What It Does|
|-----------|-----------|
|.read(size=-1)|This reads from the file based on the number of size bytes. If no argument is passed or None or -1 is passed, then the entire file is read.|
|.readline(size=-1)|This reads at most size number of characters from the line. This continues to the end of the line and then wraps back around. If no argument is passed or None or -1 is passed, then the entire line (or rest of the line) is read.|
|.readlines()|This reads the remaining lines from the file object and returns them as a list.|
	
	
here is some example :
``` 
with open('dog_breeds.txt', 'r') as reader:
# Read & print the entire file
print(reader.read())

 with open('dog_breeds.txt', 'r') as reader:
# Read & print the first 5 characters of the line 5 times
print(reader.readline(5))
f = open('dog_breeds.txt')
f.readlines()  # Returns a list object
````
Iterating Over Each Line in the File
 by .readline() method 
or .readlines or 
```
>>> with open('dog_breeds.txt', 'r') as reader:
>>>     # Read and print the entire file line by line
>>>     for line in reader:
>>>         print(line, end='')
Pug
Jack Russell Terrier
English Springer Spaniel
German Shepherd
Staffordshire Bull Terrier
Cavalier King Charles Spaniel
Golden Retriever
West Highland White Terrier
Boxer
Border Terrier
````
#### haw can we writing files. ?

|Method|	What It Does|
|-----------|-------------|
| .write(string) |This writes the string to the file.|
|.writelines(seq) | This writes the sequence to the file. No line endings are appended to each sequence item. It’s up to you to add the appropriate line ending(s).|
	
	
``` 
with open('dog_breeds.txt', 'r') as reader:
    # Note: readlines doesn't trim the line endings
    dog_breeds = reader.readlines()

with open('dog_breeds_reversed.txt', 'w') as writer:
    # Alternatively you could use
    # writer.writelines(reversed(dog_breeds))

    # Write the dog breeds to the file in reversed order
    for breed in reversed(dog_breeds):
        writer.write(breed)
````

Working With Bytes

This is done by adding the 'b' character to the mode argument. 
```
>>> with open('dog_breeds.txt', 'rb') as reader:
>>>     print(reader.readline())

Tips and Tricks
__file__

“the pathname of the file from which the module was loaded, if it was loaded from a file.” (Source"


example :
``` 
> python main.py
tests/test_commanding.py Started:
tests/test_commanding.py Passed!
tests/test_power.py Started:
tests/test_power.py Passed!
tests/test_wireHousing.py Started:
tests/test_wireHousing.py Failed!
tests/test_leds.py Started:
tests/test_leds.py Passed!


Appending to a File

append to a file or start writing at the end of an already populated file. This is easily done by using the 'a' character for the mode argument:

Working With Two Files at the Same Time
``` 
d_path = 'dog_breeds.txt'
d_r_path = 'dog_breeds_reversed.txt'
with open(d_path, 'r') as reader, open(d_r_path, 'w') as writer:
    dog_breeds = reader.readlines()
    writer.writelines(reversed(dog_breeds))

``` 


Creating Your Own Context Manager

 by placing it inside a custom class. using the with statement, you shoud add some method (__enter__ and __exit__. )
 
 
resource:
* [Read & Write Files in Python](https://realpython.com/read-write-files-python/) 
* [Exceptions in Python]([---](https://realpython.com/python-exceptions/))
* [Read & Write Files in Python - Companion Video]([---](https://realpython.com/courses/reading-and-writing-files-python/))
* [Reading and Writing Files in Python Quiz]([---](https://realpython.com/quizzes/read-write-files-python/))
