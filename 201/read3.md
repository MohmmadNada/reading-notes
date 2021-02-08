# Lists on html

## First;Ordered Lists
<ol> : 
<ol> 
<li> item1 </li>
<li> item2 </li>
<li> item3 </li

</ol>  
Second ;Unordered List
> <ul> 
><li> item1 </li>
><li> item2 </li>
><li> item3 </li>

</ul> 
third ; Definition Lists
 <dl> 
<dt> definition term </dt>
<dd> content  </dd>
<dt> definition term2 </dt>
<dd> content  </dd>

</dl>  

4th;nasted lists

if we have list inside list items 
 <ul>
<li>
item 
<li>
secondary item 
</li>

</li>
</ul>





## Boxes Dimensions  ,
#### content in html look like boxes , have dimension depnd on content , here we need to change it by:
***properties ; width and hight by pixels and percentage***
limiting width and hight ; relative browser window
 td.description {
min-width: 450px;
max-width: 650px;
min-height: 10px;
max-height: 30px;

### if the box can not content all things?

overflow ,It can have one of two values:
1. hidden ; hidden any extrra content 
2. scroll ; add scroll option so user can scroll and show every thing 







# Border, Margin & Padding

### these prperties useful for make spaces in pages . 

Border width this property has value of : pixels or (thin,medium or thick)

1. border-style 
has many values : solid,dotted, dashed, double, groove., ridge ... etc
2. border-color

we can put all in shortcut 
 p {
width: 250px;
border: 3px dotted #0088dd;} 


#### padding and margion
we can control it by width and hight or percentage 



#### centering content 

set the left-margin and right-margin to auto. then width the box 

Hiding Boxes by visibility property  
vules : hidden or visible

 css  we can use other features like 
 border-image , box-shadow and 
border-raduis






## Basic JavaScript Instructions”
ARRAYS : variable stores a list of values
we use it when we do not know haw many items we have in list 
''' varName = ['value1' , 'value2']; ''' 
numbering items star from 0 not 1 (index) ,
we can change items and acces it any time 
''' arrayName = [index numbe ];











## Decisions and Loops
#### Switch statement  
use like if , check line by line if it true then break , go out the switch , if not match ny of them , run defult case 

 switch (level) {
case 'O ne ':
title= 'Level 1 ' ;
break;
case 'Two':
tit 1 e = ' Level 2 ' ;
break;
case ' Three' :
title = 'Level 3' ;
break ;
default :
title= 'Test';
}  


#### loops , to check condition if it true , code will run it it false it will check next condition 
loops type :
1. for 
2. while (dont know how many timw code will running )3.do while 

> note :Loops are very helpful when
dealing with arrays if you want to
run the same code for each item
in the array.
note :Loops are very helpful when
dealing with arrays if you want to
run the same code for each item
in the array.
