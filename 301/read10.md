# Call stack
call stack is a mechanism for an interpreter for calls multiple functions , what function is currently being run and what functions are called from within that function, etc. 
In summary, then, we start with an empty Call Stack. Whenever we invoke a function, it is automatically added to the Call Stack. Once the function has executed all of its code, it is automatically removed from the Call Stack. Ultimately, the Stack is empty again.

is used for function invocation (call).


## call stuck is :At the most basic level, a call stack is a data structure that uses the Last In, First Out (LIFO) principle to temporarily store and manage function invocation (call).

### Temporarily store: When a function is invoked (called), the function, its parameters, and variables are pushed into the call stack to form a stack frame. This stack frame is a memory location in the stack. The memory is cleared when the function returns as it is pop out of the stack.

## How does the call stack handle function calls?

### What causes a stack overflow?

A stack overflow occurs when there is a recursive function (a function that calls itself) without an exit point. The browser (hosting environment) has a maximum stack call that it can accomodate before throwing a stack error.

        function callMyself(){
          callMyself();
        }

        callMyself();



#### The key takeaways from the call stack are:
1. It is single-threaded. Meaning it can only do one thing at a time.
2. Code execution is synchronous.
3. A function invocation creates a stack frame that occupies a temporary memory.
4. It works as a LIFO — Last In, First Out data structure.




## JavaScript error messages && debugging
Most of your time as a developer is spent reading code followed by debugging that same code, most likely to be able to read it or solve an “unexpected feature” (which, joking aside, is more correctly known as a “bug”).

#### Types of error messages
1. Reference errors
This is as simple as when you try to use a variable that is not yet declared you get this type os errors.
2. Syntax errors
 this occurs when you have something that cannot be parsed in terms of syntax,
3. Range errors
Try to manipulate an object with some kind of length and give it an invalid length and this kind of errors will show up.

4. Type errors
Like the name indicates, this types of errors show up when the types (number, string and so on) you are trying to use or access are incompatible, like accessing a property in an undefined type of variable.

# Debugging

the easiest and maybe the most common way its to simply console.log() the variables you want to check or, by using chrome developer tools, open your page with your JS code, choose your file to debug, click the line you wanna debug and refresh your page again (F5). You can also add conditional breakpoints by right-clicking a previous set breakpoint, 
Using Node.js with Visual Studio Code you can press the debug tab and add a configuration 


#### Resources
[The Call Stack defined on MDN](https://developer.mozilla.org/en-US/docs/Glossary/Call_stack)
[Understanding the JavaScript Call Stack](https://www.freecodecamp.org/news/understanding-the-javascript-call-stack-861e41ae61d4/)
[JavaScript error messages](https://codeburst.io/javascript-error-messages-debugging-d23f84f0ae7c)
[JavaScript errors reference on MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Errors)
