# Stacks and Queues
## What is a Stack
A stack is a data structure that consists of Nodes. Each Node references the next Node in the stack, but does not reference its previous.

### Stacks follow these concepts:
FILO
First In Last Out : This means that the first item added in the stack will be the last item popped out of the stack.

LIFO
This means that the last item added to the stack will be the first item popped out of the stack.

![visiual](../images/REAd10.png)

### Push O(1)
O(1)
When adding a Node, you push it into the stack by assigning it as the new top, with its next property equal to the original top.
steps : 
1.  you should have the Node that you want to add. Here is an example of a Node that we want to add to the stack.
2. you need to assign the next property 
3.  re-assign our reference top to the newly added Node, Node 5.

push pseudocode
```
ALOGORITHM push(value)
// INPUT <-- value to add, wrapped in Node internally
// OUTPUT <-- none
   node = new Node(value)
   node.next <-- Top
   top <-- Node
```
### Pop O(1)
steps :
1. create a reference named temp that points to the same Node that top points to.
2. re-assign top
3.  clear out the next property in your current temp reference
4. return the value of the temp Node that was just popped off.

pseudocode for a pop
```
ALGORITHM pop()
// INPUT <-- No input
// OUTPUT <-- value of top Node in stack
// EXCEPTION if stack is empty

   Node temp <-- top
   top <-- top.next
   temp.next <-- null
   return temp.value

```
### Peek O(1)
must be check if empty 
pseudocode for a peek
```

ALGORITHM peek()
// INPUT <-- none
// OUTPUT <-- value of top Node in stack
// EXCEPTION if stack is empty

   return top.value
```
### IsEmpty O(1)
 pseudocode for isEmpty
```
ALGORITHM isEmpty()
// INPUT <-- none
// OUTPUT <-- boolean

return top = NULL

```
## What is a Queue

terminology 
1. Enqueue - Nodes or items that are added to the queue.
2. Dequeue - Nodes or items that are removed from the queue. If called when the queue is empty an exception will be raised.
3. Front - This is the front/first Node of the queue.
4. Rear - This is the rear/last Node of the queue.
5. Peek - When you peek you will view the value of the front Node in the queue. If called when the queue is empty an exception will be raised.
5 IsEmpty - returns true when queue is empty otherwise returns false.

#### FIFO
First In First Out

#### LILO

Queue Visualization
![Queue Visualization](../images/read10_02.png)

### Enqueue O(1)
add an item to a queue 

process :
1. change the next property of Node 4 to point to the Node we are adding. 
2. re-assign the rear reference to point 

pseudocode for the enqueue
```
ALGORITHM enqueue(value)
// INPUT <-- value to add to queue (will be wrapped in Node internally)
// OUTPUT <-- none
   node = new Node(value)
   rear.next <-- node
   rear <-- node
```

### Dequeue O(1)

remove an item from a queue, always just removing the front Node of the queue. check isEmpty ?
process  : 
1.  create a temporary reference type named temp point to front 
2. re-assign front to the next value that the Node front
3. re-assign the next property on the temp Node to null.
4. return the value of the temp Node that was just removed.

pseudocode for the dequeue

```
ALGORITHM dequeue()
// INPUT <-- none
// OUTPUT <-- value of the removed Node
// EXCEPTION if queue is empty

   Node temp <-- front
   front <-- front.next
   temp.next <-- null

   return temp.value
```

### Peek O(1)
inspecting the front Node of the queue.

pseudocode for a peek
```
ALGORITHM peek()
// INPUT <-- none
// OUTPUT <-- value of the front Node in Queue
// EXCEPTION if Queue is empty

   return front.value
```
> note :  do not re-assign the next property when we peek because we want to keep the reference to the next Node in the queue.

### IsEmpty O(1)

pseudocode for isEmpty
```
ALGORITHM isEmpty()
// INPUT <-- none
// OUTPUT <-- boolean

return front = NULL
```

* [Stacks and Queues](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-10/resources/stacks_and_queues.html)