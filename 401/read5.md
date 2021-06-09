# Linked Lists
### What is a Linked List
A Linked List is a sequence of Nodes that are connected/linked to each other.

Visioal :
![linked](../images/read5.png)

### Traversal:
When traversing a linked list, you are not able to use a foreach or for loop. we use (Next ), the besst way while loop 
and check next if exicest 

Traversal Example
```
ALGORITHM Includes (value)
// INPUT <-- integer value
// OUTPUT <-- boolean

  Current <-- Head

  WHILE Current is not NULL
    IF Current.Value is equal to value
      return TRUE

    Current <-- Current.Next

  return FALSE
```
### Haw we can Add ?
Add() method will define what the value of the Node will be.newNode.Next by default is set to (null),,
``` 
ALGORITHM Add(newValue)
// INPUT <-- Value to add
// OUTPUT <-- No output

  newNode <-- NEW Node
  newNode.Value <-- newValue
  newNode.Next <-- Head
  Head <-- newNode
```
the same process for remove ...etc 
Resources:
[What’s a Linked List, Anyway pt1](https://medium.com/basecs/whats-a-linked-list-anyway-part-1-d8b7e6508b9d)

[What’s a Linked List, Anyway pt2](https://medium.com/basecs/whats-a-linked-list-anyway-part-2-131d96f71996)

[Linked Lists]([000](https://codefellows.github.io/common_curriculum/data_structures_and_algorithms/Code_401/class-05/resources/singly_linked_list.html))