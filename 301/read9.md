# Concepts of Functional Programming in Javascript
## What is functional programming?

Functional programming is a programming paradigm — a style of building the structure and elements of computer programs — that treats computation as the evaluation of mathematical functions and avoids changing-state and mutable data.

### Pure functions
1. It returns the same result if given the same arguments
2. mist be without Reading Files 

3. without Random number generation
4. It does not cause any observable side effects(modifying a global object or a parameter passed by reference.)


### Pure functions benefits
The code’s definitely easier to test.
,Unchanging over time or unable to be changed.


### Referential transparency
Basically, if a function consistently yields the same result for the same input, it is referentially transparent.
    pure functions + immutable data = referential transparency



### Functions as first-class entities
The idea of functions as first-class entities is that functions are also treated as values and used as data.

### Higher-order functions
function that either 
takes one or more functions as arguments, or
returns a function as its result
> examples :Filter,,MapReduce


### Refactoring JavaScript for Performance and Readability (with Examples!)
##### Strategies:
1. Return early from functions:
2. Cache variables so functions can be read like sentences:
3. Check for Web APIs before implementing your own functionality:
