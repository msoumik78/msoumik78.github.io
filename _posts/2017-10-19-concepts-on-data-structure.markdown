|layout|title|date|categories|
|---|---|---|---|
|post|"Data Structure Concepts"|2017-10-19 12:30:00 +0530|jekyll update| 


# Lists

Lists are of 2 types – ArrayList and LinkedList.  In Java, Arraylists are simply dynamic arrays.JDK's linked list implementation is a double linked list. Linkedlists are faster for insert / update operations (as the pointer to the next element) only needs to be changed. However get operations are faster in ArrayList (O (1)) than in LinkedList (O(n)).If you want to find the middle element of a linked list, you have to take 2 counters – the second counter incrementing after alternate iterations. If you want to find the third last element of a linked list – you have to take 2 counter where the second counter increments after every 2 operations of the first counter.

# Stacks & Queues

Stacks and Queues are two other important data structures. Stacks are LIFO and Queues are FIFO.Stack implementation in JDK is java.util.Stack.


# Tree

A tree data structure can have any nodes, a binary tree has 2 nodes, a binary search tree (BST) is one where the left node contains a value less than the parent and the right node contains a value more than the parent node.


# Algorithms

Can be of 3 main types – Dynamic programming, Divide and Conquer (like merge sort), Greedy algorithm

Following are the easy sorting but they take time (O(n2))
* Insertion sort
* Bubble sort

Following are the easy sorting but they take time (O(n))
* Selection Sort
* Quick Sort
