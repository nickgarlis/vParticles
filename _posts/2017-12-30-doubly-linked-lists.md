---
title: "Swap nodes in a Doubly Linked List"
tags:
  - "C"
  - "Nodes"
categories:
  - "Data stuctures"
---
When I first learned about Doubly Linked Lists what I found really tricky about them was how to sort them and more specifically how to swap two nodes. So I decided to make a post about it.

Let's assume that our list consists of only 4 nodes. Those are enough for us to cover every possible scenario during swapping.

Our swap function is going to take two parameters, our left and right nodes.

`void swap(struct list* left, struct list* right)`   

Before we start messing with **left** and **right's** pointers we have to make sure that the Nodes pointing to them are updated.

First we make sure that there is a Node that has **left** as next `if ( left->previous )` then we make that Node to have **right** as next `left->previous->next = right;`. If however, there are no nodes before **left** that means that it is the **head**. In that case, we now have to set our **head** equal to **right** `head = right;` since **left** is going to no longer be the **head** after the swap.

```c
  if ( left->previous ){
    left->previous->next = right;
  }
  else {
    head = right;
  }
```

We follow a similar procedure for the Node after **right**.

```c
  if ( right->next ){
    right->next->previous = left;
  }
```

Now it's just **left** and **right**. We now simply need to swap **left** and **right's** pointers.

```c
  left->next  = right->next;
  right->previous = left->previous;
  right->next = left;
  left->previous = right;
```

Notice how I assigned **left** to be **right's** next Node and **right** to be **left's** previous Node.
