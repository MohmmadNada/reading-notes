# Readings: Game of Greed 2
## Global Scope
the notions of global scope and global names are tightly associated with module files , called module scope.
by defult you are in main , you can say that your main global scope is the scope of ``` __main__ ```

you can see what inside global scope by type ```dir()```
You can access or reference the value of any global name from any place in your code. 

when we try to update global var inside fun ,
. What happens here is that when you run the body of func(), Python decides that var is a local variable because it’s assigned within the function scope. This isn’t a bug, but a design choice. Python assumes that names assigned in the body of a function are local to that function.

> Note: Global names can be updated or modified from any place in your global Python scope. Beyond that, the global statement can be used to modify global names from almost any place in your code, as you’ll see in The global Statement.

## Functions: The Local Scope
 Every time you call a function, you’re also creating a new local scope.

By default, parameters and names that you assign inside a function exist only within the function or local scope associated with the function call. When the function returns, the local scope is destroyed and the names are forgotten

you can check what inside fun scope by , __code__ ; attribute that holds information on the function’s internal code.

Resources:
* [Python Scope](https://realpython.com/python-scope-legb-rule/)
[Don’t be CONFUSED by BIG O notation anymore!]()
(Rolling Dice Examples)[https://www.youtube.com/watch?v=5Uqawfl0VHQ]
(Rolling Dice Examples)[https://artofproblemsolving.com/wiki/index.php/Basic_Programming_With_Python#Program_Example_1_3]