# java Error Handing ans debugguing 

## EXECUTION CONTEXT
every statment live in 
GLOBAL CONTEXT , FUNCTION CONTEXT or EVAL CONTEXT (NOT SHOWN)

## VARIABLE SCOPE
1. GLOBAL SCOPE ; outside {}
2. FUNCTION-LEVEL SCOPE{in}

#### throws an exception: it is going through the stack looking for errorhandling code until it gets to the global context.
#### If there is still no error handler, the script stops running and the Error object is created.

## Error object: contain 
name , message, file Number and line Number.
types: Error,Syntax Error, Reference Error,TypeError, Range Error ,URI Error and Eval Error

## ERROR OBJECTS CONTINUED
Syntax Error :incorrect use of the rules of the language.
Reference Error : variable that is not declared or is out of scope
EvalError
EvalError:INCORRECT USE OF URI FUNCTIONS
#### Type Error:
RangeError :call a function using numbers outside of its accepted range.

## Now, how we can deal with error ? 
1. DEBUG THE SCRIPT TO FIX ERRORS

2. HANDLE ERRORS GRACEFULLY
* Look at the error message, know the line and error message 
* check lines by cosole 
* know where the error , break code to the part and check 

> Note : You can also just type code into the console and it will show you a result.

* WRITING FROM THE SCRIPT TO THE CONSOLE
### write data from a script to the console, tell you how far a script has run and what values it has receivedWriting out variables lets you see what va lues the interpreterholds for them

## More with cosole 
GROUPING messages ; to check group data 
Writing tabular data 
WRITING ON A CONDITION(cosole.assert)

### Breakpoints : to pause the execution of script  by click on line number  , you can use multi breakpoints and check one by one 

>the way commonly use for find an error is by handle try, catch, finally statements Use >them to give your users helpful feedback.