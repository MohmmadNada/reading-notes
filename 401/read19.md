# Automation
## Python Regular Expression Tutorial
Regular Expressions, often shortened as regex

### Regular Expressions in Python
first ; you have to import laibrary
```
import re
```
### Basic Patterns: Ordinary Characters

Ordinary characters can be used to perform simple exact matches:

The match() function returns a match object if the text matches the pattern. Otherwise, it returns None. The re module also contains several other functions,
```
pattern = r"Cookie"
sequence = "Cookie"
if re.match(pattern, sequence):
    print("Match!")
else: print("Not a match!")
# output //Match
```
Do you notice the r at the start of the pattern Cookie?
This is called a raw string literal. It changes how the string literal is interpreted. Such literals are stored as they appear.

For example, \ is just a backslash when prefixed with an r rather than being interpreted as an escape sequence. You will see what this means with special characters. Sometimes, the syntax involves backslash-escaped characters, and to prevent these characters from being interpreted as escape sequences; you use the raw r prefix.

### Wild Card Characters: Special Characters
Special characters are characters that do not match themselves as seen but have a special meaning when used in a regular expression.

. - A period. Matches any single character except the newline character.
```
re.search(r'Co.k.e', 'Cookie').group()
'Cookie'
```
^ - A caret. Matches the start of the string.

```
re.search(r'^Eat', "Eat cake!").group()

## However, the code below will not give the same result. Try it for yourself:
# re.search(r'^eat', "Let's eat cake!").group()
'Eat'

```
$ - Matches the end of string.

[abc] - Matches a or b or c.
[a-zA-Z0-9] - Matches any letter from (a to z) or (A to Z) or (0 to 9).


\ - Backslash.
Perhaps, the most diverse metacharacter!!

If the character following the backslash is a recognized escape character, then the special meaning of the term is taken (Scenario 1)
Else if the character following the \ is not a recognized escape character, then the \ is treated like any other character and passed through (Scenario 2).
\ can be used in front of all the metacharacters to remove their special meaning (Scenario 3).

Resources :
* [Python Regular Expressions Tutorial](https://www.datacamp.com/community/tutorials/python-regular-expression-tutorial)
* [shutil](https://pymotw.com/3/shutil/)
* [Automation Ideas](https://www.youtube.com/watch?v=qbW6FRbaSl0&t=69s)
* [Automating Your Browser and Desktop Apps](https://www.youtube.com/watch?v=dZLyfbSQPXI)
* [Watchdog](https://pythonhosted.org/watchdog/)