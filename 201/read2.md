# Chapter 2
2## Text in html
1. Headings 
<h1></h1>
2. Paragraphs
<p> </p>
3. Bold <b></b>
4. italic <i></i>
5.
## Superscript
#### tag sup  , pour of 
#### tag sub , CO2
6. brak tag 
br 
7. horizontal rule  
hr
if we have more than one space between words , it will show one space (white space collapsing.)

''' </p> ''' empty tag

### Visual Editors & Their Code views
Visual Editors : mainly all editors have the same features
Code views :
show you the code created by the visual editor

###semantic markup.
did not affect the
structure of your web pages, but they do add extra information about page 
its helpful for search engine


## Emphasis and string

''' <strong> use for strong importance., show bold text strong importance </strong > '''
''' <em>emphasis that subtly changes
the meaning of a sentence. and show it italic</em>

## Quotations
1. blockquote tag  for longer quotes
2. q  tag for shorter quotes

# abbreviations & Acronyms.
<abbr> </abbr> 
# Citations & Definitions
''' <cite> ''' 
''' <dfn> '''

# Author Details
<address>
<p><a href="mailto:homer@example.org">
homer@example.org</a></p>
<p>742 Evergreen Terrace, Springfield.</p>
</address>

#Changes to Content
''' <p>It was the <del>worst</del> <ins>best</ins> idea
she had ever had.</p>

or use <s></s> ''' 

# Chapter 10
##Introducing CSS
### how css work ?
###### imagine that there is an invisible box around every HTML element.

#### rules :selector and a declaration{property and a value}.
p {selector and a declaration.}

## Using External CSS
link 
'''
<link href="css/styles.css" type="text/css"
rel="stylesheet" /
'''
## Using Internal CSS
inside head ''' <style type="text/css">
**** '''


## CSS Selectors
mainly by class , id , element name ... etc 

##How Css Rules Cascade
remeber this points :
LAST RULE
specific
!important

##Why use External Style Sheets?
css run once , so we get faster website 
easy to edit 

# JavaScript
##chapter
####script is a series of instructions that follow one by one , every one is a statment every statment ends with semicolon 
#### code blocks ; have more than one 
statment with curly brace is not follow with semicolon.
#### comments '''  /* comment */ 
// comment ''' 

note :JavaScript codeis green
Multi-line comments are pink
Single-line comments are gray

###WHAT IS A VARIABLE?
the storge where we can store data in 
we declaretion them by : 
''' var Name ; ''' 
we assign it in form 
''' Name  =  5 ; ''' 
### data type in JS are : 
1. NUMERIC
2. STRING
3. BOOLEAN 
boolean have true or false value 
####how we can name the variable ?
we have rules for that :
1.could not start name with number 
2. we can use $ and _ , do not use - or . 
3. no command name like var 
4. Score and score did not the same 
5.the name should be meanningful
6. if you have more than one latter use camel case 

### array its a variable it stores a list of values.

var colors;
''' colors = ['white', 'black', ' custom '];

var colors =new Array('white ' ,
'black',
'custom ' ); ''' 
''' var itemThree;
itemThree = col ors [ 2] ;''' 
the last code declead index 3 

## opereters 
Comparison Operators; evaluateing condation 
==(is equal to) compare value only 
!= (is not equal to) compare value only 
=== (is  equal to) compare value and data type 
!== (is not equal to) compare value and data type 
< Greater than 
> Less than
>= Greater than or equal 
<= Less than or equal

expression : 
single value like : var abc = 5;
operators calculate the value : 


### Decisions and Loops
  JavaScript is an asynchronous, dynamically-typed, interpreted scripting language, designed to make web pages dynamic and interactive. 
  a == b 
if (a - b > 0) {
  val = a - b;
} else {
  val = b - a;
} 
< less than 
> greater thaan 
<= less than or equal to 
>= Grater than or equal to 



we can use more than one comparison operators , calls this case logical operators 
and , I I or ! not 


note : logical experssions are evaluated from left to right 
if the left side give enough info. to get the answer , no need to evaluate right side . 


Loops check condition; check the condition if true it will be check again until check condition returns false . 
type loops : 
FOR (limiting time ) and while( until the condition is false ) and do while 
 

 General form (for)
  for (var i = 0 ; i < 10;i--  ) {
      var s = i +  5;
  }

 General form (while
 while (i < 10) {
msg += i + ' x 5 = ' + (i * 5) + '<br I>';
i++;) ;
 }


  JavaScript is an asynchronous, dynamically-typed, interpreted scripting language, designed to make web pages dynamic and interactive. 
  a == b 
if (a - b > 0) {
  val = a - b;
} else {
  val = b - a;
} 
'''
< less than 
> greater thaan 
<= less than or equal to 
>= Grater than or equal to '''



we can use more than one comparison operators , calls this case logical operators 
and , I I or ! not 


note : logical experssions are evaluated from left to right 
if the left side give enough info. to get the answer , no need to evaluate right side . 


Loops check condition; check the condition if true it will be check again until check condition returns false . 
type loops : 
FOR (limiting time ) and while( until the condition is false ) and do while 
 
