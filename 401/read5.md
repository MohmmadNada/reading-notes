#                   Lambda
### What is Lambda

A lambda function is a small anonymous function.
A lambda function can take any number of arguments, but can only have one expression.

### Why we use it ?

They are useful in allowing quick calculations or processing as the input to other functions.

Lambda functions are used for functional programming.

They can be useful as quick, throwaway single line functions. 



###  What does it look like
1. live without lambda

```
>>> def identity(x):
...     return x
```
2.  live with lambda
```
#lambda arguments : expression
# The expression is executed and the result is returned:
x = lambda a : a + 10
print(x(5))
# result ::: 15 
```
it is can take more than one argument 
```
x = lambda a, b : a * b
print(x(5, 6))
# output // 30
```
What does it look like
> (lambda x: x + 1)(2) = lambda 2: 2 + 1
>                    = 2 + 1
>                    = 3



Say you have a function definition that takes one argument, and that argument will be multiplied with an unknown number:

```
def myfunc(n):
  return lambda a : a * n

mydoubler = myfunc(2)

print(mydoubler(11)) //output 22
```
```
def myfunc(n):
  return lambda a : a * n

mydoubler = myfunc(2)
mytripler = myfunc(3)

print(mydoubler(11))#putput //22
print(mytripler(11)) #putput //33
```
###  Do you know , What Anonymous Functions is ?
let us take a look on Anonymous Functions ; 

 an anonymous function is a function without a name , we use it in python (lambda )


###  Can you use recursion with lamda ?
 look to this code 
```
>>> high_ord_func = lambda x, func: x + func(x)
>>> high_ord_func(2, lambda x: x * x)
6
>>> high_ord_func(2, lambda x: x + 3)
7
```
###  watch this vedio 
> https://www.youtube.com/watch?v=xTtwkfGLGus

###  Quick Quiz:

 What is the output of the following code snippet?
hint :A lambda function can’t contain the return statement.

1. func = lambda x: return x
print(func(2)) 

// invalid syntax
2.  (lambda x: (x + 3) * 5 / 2)(3)
 


