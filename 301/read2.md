# JQUERY
### FIND ELEMENT BY CSS style and do somthing with it by jquery methods 
1. must add script 
2. add code in javascript file 
### its about write less do more 
    $('element').code('')

it give the elemt index 
if we have more than one selected element and we need get info. from it , it will deal with the first one , if we want to set data we will give it to all 

### looping
we can use jquery to code more than item in one line 

### chaining
you can list several methods at a time
using dot notation to separate
each one

    $( 'l i [i d!="one"] ') . hide() .delay(SOO) . fadeln(1400);

### the load event ()
it is run after after all resources 
ready 
check the browser supports DOContent kadded 

>note : script tag should be before closing body tag 

### getting element content 
by .html and .text methods 

### updating elements 
we can get it by 
1. .html()
2. .text()
3. .remove()
4. .replaceWith()

### Inserting new elements
1. Create the new elements in a jQuery object
    <li>element:var $newFragment = $('<li>'};

2. Use a method to insert the content into the page
1. .before()
2. .after()
3. .append()
4. .prepend()

### GETTING AND SETTING ATTRIBUTE VALUES
1. .attr()
2. .removeAttr()
3. .addClass()
4. .rempveClass()
